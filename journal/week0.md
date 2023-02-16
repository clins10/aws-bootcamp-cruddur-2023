# Week 0 — Billing and Architecture

## Required Homework/Tasks

### Install AWS CLI and ensure that it works

I already installed the AWS CLI before now, running the **msiexec** command to run the **MSI installer**, as specified on the [AWS CLI installation Documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

```bash
    msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```
To **confirm the installation** i ran the command below
    
```bash
    aws --version
``` 
And got the output below
    
![screen shot of aws-version](/images/aws-version.PNG)

To prove that my AWS credential were setup correctly i ran the comand below
    
```bash
    aws sts get-caller-identity
```
And got the output below

![screen shot of aws-sts](/images/awscli-ID.PNG)

### Create A Billing Alarm

I created a billing alarm for my AWS account, and set it to send me an email when my expenses is less than or equal $1.00

![screen shot of billing alarm](/images/billing-alarm.PNG)

### Create a Budget Report

I created a billing report for my AWS account, and set it to send me an email when my expenses goes beyond $1.00

![screen shot of billing report](/images/budgets.PNG)




## Homework Challenges

