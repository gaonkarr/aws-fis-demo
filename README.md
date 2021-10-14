
# AWS Fault Injection Simulator sample demo

- [AWS Fault Injection Simulator sample demo](#aws-fault-injection-simulator-sample-demo)
- [Important!](#important)
  - [Pre-requisites](#pre-requisites)
  - [Demo 1 : Stop random EC2 instances using Tags](#demo-1--stop-random-ec2-instances-using-tags)
  - [Demo 2 : Stop random EC2 instances using Tags and Alarms](#demo-2--stop-random-ec2-instances-using-tags-and-alarms)
  - [Demo 3 : Stop random EC2 instances using Tags, Alarms and Filters](#demo-3--stop-random-ec2-instances-using-tags-alarms-and-filters)
  - [Demo 4 : Stop random EC2 instances using SSM](#demo-4--stop-random-ec2-instances-using-ssm)
  - [Clean up](#clean-up)
  - [References and more](#references-and-more)


AWS Fault Injection Simulator (AWS FIS) is a managed service that enables you to perform fault injection experiments on your AWS workloads. Fault injection is based on the principles of chaos engineering. These experiments stress an application by creating disruptive events so that you can observe how your application responds. You can then use this information to improve the performance and resiliency of your applications so that they behave as expected.

To use AWS FIS, you set up and run experiments that help you create the real-world conditions needed to uncover application issues that can be difficult to find otherwise. AWS FIS provides templates that generate disruptions, and the controls and guardrails that you need to run experiments in production, such as automatically rolling back or stopping the experiment if specific conditions are met.

# Important! 
AWS FIS carries out real actions on real AWS resources in your system. Therefore, before you use AWS FIS to run experiments in production, we strongly recommend that you complete a planning phase and run the experiments in a pre-production environment.

## Pre-requisites
To complete these demos, ensure Launch the CloudFormation template. 

This template creates following resources in your AWS Account : 
1. 


## Demo 1 : Stop random EC2 instances using Tags
## Demo 2 : Stop random EC2 instances using Tags and Alarms
## Demo 3 : Stop random EC2 instances using Tags, Alarms and Filters
## Demo 4 : Stop random EC2 instances using SSM

## Clean up

Remember to delete all the resources once you are done testing.


## References and more

