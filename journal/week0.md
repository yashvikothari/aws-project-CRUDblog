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

# Expectation

| week No. | Outcome                                           | Business Scenario                                | Possible Spend Considerations                                               | Security Considerations | Alternative Considerations | Challenges                                                                                                                              |
|----------|---------------------------------------------------|--------------------------------------------------|-----------------------------------------------------------------------------|-------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| 0        | build useful architecture diagrams                | propose implementation architecture              | what spend company expect to encounter.                                     | …                       | …                          | -Destroying your root account credentials                                                                                               |
|          | Walkthrough for cost of AWS common cloud services | get it reviewed by our fractional CTO            | how to ensure we keep our spending low.                                     |                         |                            |                                                                                                                                         |
|          | AWS meter-billing                                 | include technical architecture diagram           | initial assumption :                                                        |                         |                            | -Set MFA, IAM role                                                                                                                      |
|          |                                                   | breakdown possible services & give justification | 1. a credit card to activate your AWS Account.                              |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  | 2. AWS account  > 12 months, free-tier for some services won't be available |                         |                            | -Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.                          |
|          |                                                   |                                                  | 3. check with sales team for AWS Credits program                            |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                             |                         |                            | -Review all the questions of each pillars in the Well Architected Tool (No specialized lens)                                            |
|          |                                                   |                                                  |                                                                             |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                             |                         |                            | -Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts                               |
|          |                                                   |                                                  |                                                                             |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                             |                         |                            | -Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility. |
|          |                                                   |                                                  |                                                                             |                         |                            |                                                                                                                                         |
|          |                                                   |                                                  |                                                                             |                         |                            | -Open a support ticket and request a service limit                                                                                      |
| 1        |                                                   |                                                  |                                                                             |                         |                            |                                                                                                                                         |

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
