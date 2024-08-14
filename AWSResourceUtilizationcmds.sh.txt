#!/bin/bash

#########
# Author:Anu
# purpose : report aws resource usage using AWS CLI commands from AWS EC2
##########

set -x #debug mode
set -e #exit when it has errors
set -o pipefail  #exit when it has errors even with pipe

#list s3 buckets
aws s3 ls

#list EC2 Instances
# aws ec2 describe-instance  #very huge data so use below script
aws ec2 describe-instance | jq '.Reservations[].Instances[].InstanceId' #jq JSON Parser

#list lambda
aws lambda list-functions

#list IAM Users
aws iam list-users

:wq!


