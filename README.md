# AWS Engineering Learning Series - EKS
## Labs

- [Lab 1 - Building a Docker Image](./labs/01-docker)
- [Lab 2 - Introduction to Pods](./labs/02-pods)
- [Lab 3 - Labeling our Pods](./labs/03-labels)
- [Lab 4 - Deployments](./labs/04-deployments)
- [Lab 5 - Services](./labs/05-services)


## Launching your Lab Environment

Follow the below steps to get setup with a Cloud9 environment and create your Cluster.

## 1. Launch a Cloud9 Environment

This will be where you'll be performing the labs throughout the sessions.

Click the button to begin creating a CloudFormation stack for the region you are assigned.

Preferably right click an open it in a new tab.

| Region          | CloudFormation     |
| --------------- |:------------------:|
| eu-central-1 (Frankfurt)       | [![Launch Stack]([https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=cloud9&templateURL=https://awsrebooteks.s3.us-east-1.amazonaws.com/cloud9-template.yaml](https://awsrebooteks.s3.us-east-1.amazonaws.com/cfn.yml?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEEgaCXVzLWVhc3QtMSJHMEUCIQCDG9EIFg0MTA%2BQXAdMvKlwO4C2lQPzndZizBybr2%2B1oQIgLgmEvv3j3n%2BG15ayztV2mjX7ZqKsRTjXckJSUIxQLmsq5QIIcRAAGgw4MjM5MTk1NzYzODEiDII7nMjXdjE2tXkoFSrCArGPSgacKgjgTzxgSW%2F6ddWgIA2Rz%2BuevMZt7MRuChd%2BHVN1sJretUKi6sufvLVHmZNMLXGoQfTY5JcquEjOK2FfXAdNjT2QFvIHFkGQh7gn%2BslGNN%2B4gAHgUGpyI3Smuisq0V5PLrNUFFuAz4OY9RDZ8FpotXx00HzD3qUOUm6lWlu6i7l9ks9BANRZP0CBWBlrcWIL%2F%2B4IzKB1s9om0Exi9%2BDdJCy91QcVeDO0wBl6CHkTvW4O%2FTlip9%2BAkNf3T5XrRIDXSwakn8273cU6pd18D3F2X%2Fpb%2BSlUWp69vewrMoVMBWomHda2gZIpBaPDaZZTeZDssZZPa14BMW64mraOeRfYD%2FhniN%2FC8jtxiYbbsPCVuRMSSY3sgZS%2FXRs5NJUiwBnsGt30klLe4%2FcL5OP4Byk3988s5UgkQt6e%2FKXzGuwwgtOcowY6hwLsd0g%2BkVjucBYJP%2FQdtW99p%2ByAsYbXdRs4UOD%2B0Bsn1%2Fj%2BXZfN%2FZBRnWXcIJ7nEu9yFMFWTifUTbXXVajqFgCnRDf5SjVQSN3dSOSc3IK5POuCX5hQ6s6f77ALY2IyswbMJmHfWtbu2UdxXnlBQVzbuGA4nBBsad0dFQyEajnQFHDwplM3%2BFv89DPAjG%2Bk4lLVmlBPkI5uxf%2BeikjbD95tSw1lJZkDveVm3hjpELbul1Om3q%2Biuht1UaX9N8dC%2B3WWwmAfTqGQ4lpjP9VA6d%2Bf0VqUCBG3ihjNsEC4RJzjIfGIj1POjLd2oya17%2BkSQA9Hi7t8%2BRXpBiBtIOh3K275kCa2c3fG%2FA%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20230519T075125Z&X-Amz-SignedHeaders=host&X-Amz-Expires=43200&X-Amz-Credential=ASIA37VLPAU6ZIMP6W5F%2F20230519%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=a614a83e048fca14fcade561f757cc1748fa00d19c1b58c6aa3cfa859fa0c2f5)) |


Just before clicking "Create stack" button, please tick "I acknowledge that AWS CloudFormation might create IAM resources."

If you get stuck, the CloudFormation template is available [here](https://els-eks2020.s3-eu-west-1.amazonaws.com/cloud9-template.yaml) and also in this [repo](./cloudformation/cloud9-template.yaml).

## 2. Attach the IAM Role to the Cloud9 instance

This will allow your cloud9 environment access to perform the actions needed for the sessions.

This can be done in the EC2 console, navigate to your EC2 instances, or click the link below:

Preferably right click an open it in a new tab.

| Region          | EC2     |
| --------------- |:------------------:|
| eu-central-1 (Frankfurt)       | [Console link](https://eu-central-1.console.aws.amazon.com/ec2/v2/home?region=eu-central-1#Instances:tag:Name=cloud9;sort=instanceState) |


 * Select the Cloud9 instance
 * Click Actions > Security > Modify IAM Role
 * Filter the roles, searching for "cloud9"
 * Click Apply once the role is selected

## 3. Access your Cloud9 environment

This can be done in the Cloud9 console, navigate to Cloud9 or click the link below:

Preferably right click an open it in a new tab.


| Region          | EC2     |
| --------------- |:------------------:|
| eu-central-1 (Frankfurt)       | [Console link](https://eu-central-1.console.aws.amazon.com/cloud9/home?region=eu-central-1) |

 * Click Open IDE

## 4. Setup the Cloud9 environment

The environment will be our workstation for the sessions, there are a few steps needed to get it setup

* From within the Cloud9 environment perform the below steps:

  * Click on AWS Cloud9 Preferences > GEAR (top left) 
  * Click on AWS SETTINGS > Credentials
  * Turn off 'AWS managed temporary credentials'

* Change to a dark theme if you prefer:

  * View > Themes > UI Themes > Classic Dark

### Run the below commands in the Cloud9 terminal

#### Clone the repository

```bash
git clone https://github.com/aws-ReBOOT/eks.git
```

#### Run the bootstrap script

The script installs and configures the necessary pre-requisites

```bash
eks/scripts/bootstrap.sh
```

Confirm the IAM role is as expected

### Launching the EKS Cluster

Launch your cluster from the Cloud9 environment by running the following `eksctl` command:

```bash
eksctl create cluster --node-type t3.medium --name eks --managed
```

### Ensure that you have nodes attached

If you scaled down your cluster on Day 2 you can scale up using `eksctl` as follows:

```bash
$ eksctl get clusters
$ eksctl get nodegroup --cluster eks
$ eksctl scale nodegroup --cluster=eks --nodes=2 ng-xxxxxxx
```

# Scaling Down your Worker Nodes

Your voucher should cover the costs for the full period of the learning series but if, between sessions, you want to
prevent extra costs you can scale down your clusters using `eksctl` as follows:

```bash
$ eksctl get clusters
$ eksctl get nodegroup --cluster eks
$ eksctl scale nodegroup --cluster=eks --nodes=0 ng-xxxxxxx
```

_Note: As of 2019-09-30 there is a bug with the above command [github/issues/809](https://github.com/weaveworks/eksctl/issues/809) that does not update the min value of the auto scaling group. To get around this scale the nodes to 0, then to 1 and then to 0 again (using the last command above)._

# Cleanup (Only do this after the end of all three sessions)

After the end of all three sessions, follow the below steps to delete the EKS cluster and Cloud9 environment

## Delete all the Services

Delete all the services of type `LoadBalancer` which have provisioned ELBs in your account:

```bash
$ # List all services with type LoadBalancer
$ kubectl get svc --all-namespaces -o json \
    | jq -r '.items[] | select(.spec.type == "LoadBalancer") | .metadata.name'

# For each of the outputted services do
$ kubectl delete svc <service name>
service "<service name>" deleted
```

Then you can delete the cluster, node group and CloudFormation stack.


## Delete the EKS cluster

This can be done in the Cloud9 console, navigate to Cloud9, or click the link below:

| Region          | EC2     |
| --------------- |:------------------:|
| eu-central-1 (Frankfurt)       | [Console link](https://eu-central-1.console.aws.amazon.com/cloud9/home?region=eu-central-1) |


* Delete the EKS cluster from the Cloud9 terminal with the below command:

```bash
$ eksctl delete cluster eks
```

## Delete the Cloud9 CloudFormation stack

This can be done in the CloudFormation console, navigate to CloudFormation, or click the link below:

| Region          | EC2     |
| --------------- |:------------------:|
| eu-central-1 (Frankfurt)       | [Console link](https://eu-central-1.console.aws.amazon.com/cloudformation/home?region=eu-central-1) |


There may be a number of stacks, select the stack named "cloud9", and click the "Delete" button
