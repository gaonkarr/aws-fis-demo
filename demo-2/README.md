
# Demo 2 : Stop random EC2 instances using Tags and Alarms 

In this experiment, we will be randomly stopping instances that are tagged. We will also setup CloudWatch alarm to showcase FIS safeguard and rollback to stead state. When the CloudWatch alarm goes into Alarm state, the experiment is stopped and all instances are started automatically. This experiment is to showcase simple randomly stopping instances and then getting them back to stead state if an Alarm is raised. 

## Deployment

1. Update the IAM Role Account ID and CloudWatch Alarm in the [/demo-2/fis-stop-random-alarm.json](fis-stop-random-alarm.json). Replace _\<01234567890\>_, with your Account ID. Also, replace the _\<region\>_ with correct region.

```
"value": "arn:aws:cloudwatch:<region>:<01234567890>:alarm:NetworkInAbnormal"

"roleArn": "arn:aws:iam::<01234567890>:role/MyFISExperimentRole"

```

2. Create AWS FIS Experiment Template to randomly stop and re-start 3 random tagged instances. These instances will be automatically started in 5 mins. 

```
aws fis create-experiment-template --cli-input-json file://fis-stop-random-alarm.json
```

3. Start the AWS FIS Experiment

Copy the Experiment ID from output of command in step 2. Paste the Experiment ID in _\<experiment-template-id\>_

```
aws fis start-experiment --experiment-template-id <experiment-template-id>
```

4. Confirm that the EC2 instances have stopped.
 
5. Run the following command to manually trigger the CloudWatch Alarm. 

```
aws cloudwatch set-alarm-state --alarm-name "NetworkInAbnormal" --state-value ALARM --state-reason "testing-rollback" 
``` 


## Observe

If you are using FIS for the first time then it is easy to view the experiments in the AWS Console. 

When you start the AWS FIS Experiment, FIS will randomly stop 3 instances that are tagged with the keypair "Experiment=ChaosReady". It will wait for 5 mins before restarting the EC2 instances. 

However, we will simulate real world use-case of issue detected when instances went offline and a CloudWatch alarm is raised. As the Alarm state changes to InAlarm, FIS will stop the experiment and rollback to stead state, i.e. all instances are up and running.

![Experiment stopped by alarm](../demo2-experiment-stopped.png)
![Instances running](../demo2-instances-running.png)
