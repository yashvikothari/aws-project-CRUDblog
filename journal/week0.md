# Week 0 — Billing and Architecture

- going through platform business usecase
- taking references of architecture diagram of what we plan to build :
  1.using draw.io / Lucid Chart to build architecture diagram
  2.Reading C4 model - https://c4model.com/
- build useful architecture diagrams
- cost of common cloud services
- Running through the cloud services we will utilize
- AWS UAT & account testing
- working meter-billing with AWS
- AWS account signup and track spend in AWS
  eg . AWS Budgets, AWS Cost Explorer, Billing Alarms
- Look at monthly billing reports
- Launching AWS CloudShell and exploring AWS CLI
- Generating AWS credentials
- Documentation : HLD & LLD
  Learning and implementing mix of both
- AWS Billing
- AWS security measures.
- AWS architecture best practices.
- connect each service organically to create architecture like a 3-tier web application
- Sevices used
- prepare SOP

# Expectation

| week No. | Outcome                                           | Business Scenario                                | Possible Spend Considerations                                              | Security Considerations | Alternative Considerations | Challenges                                                                                                                              |
| -------- | ------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------------------------------- | ----------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 0        | build useful architecture diagrams                | propose implementation architecture              | what spend company expect to encounter.                                    | …                       | …                          | -Destroying your root account credentials                                                                                               |
|          | Walkthrough for cost of AWS common cloud services | get it reviewed by our fractional CTO            | how to ensure we keep our spending low.                                    |                         |                            |                                                                                                                                         |
|          | AWS meter-billing                                 | include technical architecture diagram           | initial assumption :                                                       |                         |                            | -Set MFA, IAM role                                                                                                                      |
|          |                                                   | breakdown possible services & give justification | 1. a credit card to activate your AWS Account.                             |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  | 2. AWS account > 12 months, free-tier for some services won't be available |                         |                            | -Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.                          |
|          |                                                   |                                                  | 3. check with sales team for AWS Credits program                           |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                            |                         |                            | -Review all the questions of each pillars in the Well Architected Tool (No specialized lens)                                            |
|          |                                                   |                                                  |                                                                            |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                            |                         |                            | -Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts                               |
|          |                                                   |                                                  |                                                                            |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                            |                         |                            | -Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility. |
|          |                                                   |                                                  |                                                                            |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                            |                         |                            | -Open a support ticket and request a service limit                                                                                      |
| 1        |                                                   |                                                  |                                                                            |                         |                            |                                                                                                                                         |

# Source

- suggest checking the videos that Andrew and his team put together
  https://www.youtube.com/playlist?list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv
- To do list for:

1. getting started with AWS Core Services : Compute,Storage,Networking,Security,DB & Storage.
2. do cost management labs & advance module - web appplication,to learn to connect each service organically to create architecture like a 3-tier web application.
   https://catalog.workshops.aws/general-immersionday/en-US/

# Services Used

following services:

-Github Account.
-copy Andrew's repository template to start with codebase as per standard formatting
-a Gitpod account and install the extension for your browser.
-Github CodeSpace.
-AWS account (Spin all the services here).
-Draw.io/Lucidchart Account to create chart/diagrams & overview of what are you creating.

- Create Honeycomb.io account.
- Create Rollbar account.

# Selecting AWS region based on requirements like latency,compliance,services

1.Identifying Latency is 1 need :
Cloud Ping (https://www.cloudping.info/)

2.Pricing :
Based on AWS Services for various regions pricing may vary.

3.Services :

all services want to use are available for that region.

4.Compliance :

use the region close to you and adhered by data compliance

# Billing Alerts,Tags,Cost Explorer

1.set the billing alarm so you don't have unexpected costs.
2.If using IAM user,attach billing policy otherwise won't be able to access console part else error will be incurred of not having permission

# Pricing Example

- estimate cost of aws products & Calculator
  https://calculator.aws/#/
- breaks downs the cost of each instance in each region a very good site to compare cpu's / models etc is peviously known (https://ec2instances.info) /
  (https://instances.vantage.sh/)
- consider using Cloudability/Corestack/CloudCheckr, as both are designed to provide cost management and optimization for AWS/multi-cloud environments.

-depends on how do we plan & how & what we look for :
1.getting 300,000 IOPS from locally attached Instance storage or from
an EBS volume,based on why and what usecase ?
2.Eg: AMD Milan is a codename of their CPU models.
if we consider about ec2 instances using AMD cpu's?
If so - see https://aws.amazon.com/ec2/amd/

The family type depends on what you are trying to run.

Burstable - T3a / Compute heavy - C6a / More Balanced - M6a / More Ram heavy - R6a and so on.

The latest generation are the sixth generation.
3.comparing from additional columns about Max IOPS
4.Checkout the EBS documentation on the amount of IOPS get on io2 / express EBS volume types
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html

for need local SSD's - check out c5ad instance type based on availability

And dont just fixate on IOPS as you need to see what overall throughput you need and if the instance type / size supports the amount of data you need to put through.

as per to do list, adding AWS Skill Builder Block Storage learning pathway for basics here & go into a deep dive.
If you really want to understand all these - make time to go through that :
https://explore.skillbuilder.aws/learn/lp/93/storage-learning-plan-block-storage

this way it helps really understand how to architect / answer for such questions even randomly

# SOP Week 0

## Get ready with working AWS CLI.

We use AWS CLI often.
We"ll proceed to install account.

### Install AWS CLI

- We are going to install the AWS CLI when our Gitpod enviroment lanuches.
- We are are going to set AWS CLI to use partial autoprompt mode to make it easier to debug CLI commands.
- The bash commands we are using are the same as the [AWS CLI Install Instructions]https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

Update our `.gitpod.yml` to include the following task.

```sh
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

We'll also run these commands indivually to perform the install manually

### Create a new User and Generate AWS Credentials

- Go to (IAM Users Console](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-east-1#/users) andrew create a new user
- `Enable console access` for the user
- Create a new `Admin` Group and apply `AdministratorAccess`
- Create the user and go find and click into the user
- Click on `Security Credentials` and `Create Access Key`
- Choose AWS CLI Access
- Download the CSV with the credentials

### Set Env Vars

We will set these credentials for the current bash terminal

```
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
export AWS_DEFAULT_REGION=us-east-1
```

We'll tell Gitpod to remember these credentials if we relaunch our workspaces

```
gp env AWS_ACCESS_KEY_ID=""
gp env AWS_SECRET_ACCESS_KEY=""
gp env AWS_DEFAULT_REGION=us-east-1
```

### Check that the AWS CLI is working and you are the expected user

```sh
aws sts get-caller-identity
```

You should see something like this:

```json
{
  "UserId": "AIFBZRJIQN2ONP4ET4EK4",
  "Account": "655602346534",
  "Arn": "arn:aws:iam::655602346534:user/andrewcloudcamp"
}
```

## Enable Billing

We need to turn on Billing Alerts to recieve alerts...

- In your Root Account go to the [Billing Page](https://console.aws.amazon.com/billing/)
- Under `Billing Preferences` Choose `Receive Billing Alerts`
- Save Preferences

## Creating a Billing Alarm

### Create SNS Topic

- We need an SNS topic before we create an alarm.
- The SNS topic is what will delivery us an alert when we get overbilled
- [aws sns create-topic](https://docs.aws.amazon.com/cli/latest/reference/sns/create-topic.html)

We'll create a SNS Topic

```sh
aws sns create-topic --name billing-alarm
```

which will return a TopicARN

We'll create a subscription supply the TopicARN and our Email

```sh
aws sns subscribe \
    --topic-arn TopicARN \
    --protocol email \
    --notification-endpoint your@email.com
```

Check your email and confirm the subscription

#### Create Alarm

- [aws cloudwatch put-metric-alarm](https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/put-metric-alarm.html)
- [Create an Alarm via AWS CLI](https://aws.amazon.com/premiumsupport/knowledge-center/cloudwatch-estimatedcharges-alarm/)
- We need to update the configuration json script with the TopicARN we generated earlier
- We are just a json file because --metrics is is required for expressions and so its easier to us a JSON file.

```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm_config.json
```

## Create an AWS Budget

[aws budgets create-budget](https://docs.aws.amazon.com/cli/latest/reference/budgets/create-budget.html)

Get your AWS Account ID

```sh
aws sts get-caller-identity --query Account --output text
```

- Supply your AWS Account ID
- Update the json files
- This is another case with AWS CLI its just much easier to json files due to lots of nested json

```sh
aws budgets create-budget \
    --account-id AccountID \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json
```
