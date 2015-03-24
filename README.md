http://docs.aws.amazon.com/cli/latest/reference/cloudformation/index.html#cli-aws-cloudformation



________________________________________________________________________________

| ~/workspaces/aws @ macmini (james) 

| => aws configure

AWS Access Key ID [****************VN3A]: 

AWS Secret Access Key [****************3NQ3]: 

Default region name [us-west-2a]: us-west-2

Default output format [json]: 

________________________________________________________________________________

| ~/workspaces/aws @ macmini (james) 

| => aws ec2 describe-instances 

{

    "Reservations": []

}



| ~/workspaces/aws @ macmini (james) 
| => aws cloudformation create-stack --template-body file:////Users/james/workspaces/aws/WordPress_Single_Instance_With_RDS.template --stack-name jsandlinqa1 --parameters ParameterKey=KeyName,ParameterValue=////Users/james/.ssh/aws_keypair_oregon.pem 
{
    "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644"
}

________________________________________________________________________________

| ~/workspaces/aws @ macmini (james) 

| => aws cloudformation describe-stacks

{

    "Stacks": [

        {

            "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644", 

            "Description": "AWS CloudFormation Sample Template WordPress_Single_Instance_With_RDS: WordPress is web software you can use to create a website or blog. This template installs a single-instance WordPress deployment that uses an Amazon RDS database instance for storage. It demonstrates using the AWS CloudFormation bootstrap scripts to install packages and files when an instance is launched. **WARNING** This template creates an Amazon EC2 instance and an Amazon RDS database instance. You will be billed for the AWS resources used if you create a stack from this template.", 

            "Parameters": [

                {

                    "ParameterValue": "****", 

                    "ParameterKey": "DBPassword"

                }, 

                {

                    "ParameterValue": "0.0.0.0/0", 

                    "ParameterKey": "SSHLocation"

                }, 

                {

                    "ParameterValue": "****", 

                    "ParameterKey": "DBUsername"

                }, 

                {

                    "ParameterValue": "db.t1.micro", 

                    "ParameterKey": "DBClass"

                }, 

                {

                    "ParameterValue": "wordpress", 

                    "ParameterKey": "DBName"

                }, 

                {

                    "ParameterValue": "////Users/james/.ssh/aws_keypair_oregon.pem", 

                    "ParameterKey": "KeyName"

                }, 

                {

                    "ParameterValue": "t1.micro", 

                    "ParameterKey": "InstanceType"

                }, 

                {

                    "ParameterValue": "5", 

                    "ParameterKey": "DBAllocatedStorage"

                }

            ], 

            "Tags": [], 

            "StackStatusReason": "User Initiated", 

            "CreationTime": "2015-03-24T19:37:28.569Z", 

            "StackName": "jsandlinqa1", 

            "NotificationARNs": [], 

            "StackStatus": "CREATE_IN_PROGRESS", 

            "DisableRollback": false

        }

    ]

}

| => aws cloudformation describe-stack-events --stack-name "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644"

{

    "StackEvents": [

        {

            "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644", 

            "EventId": "DBInstance-CREATE_IN_PROGRESS-1427225886209", 

            "ResourceStatus": "CREATE_IN_PROGRESS", 

            "ResourceType": "AWS::RDS::DBInstance", 

            "Timestamp": "2015-03-24T19:38:06.209Z", 

            "ResourceStatusReason": "Resource creation Initiated", 

            "StackName": "jsandlinqa1", 

            "ResourceProperties": "{\"MasterUsername\":\"****\",\"DBSecurityGroups\":[\"jsandlinqa1-dbsecuritygroup-ak62506o7m0x\"],\"DBInstanceClass\":\"db.t1.micro\",\"AllocatedStorage\":\"5\",\"DBName\":\"wordpress\",\"Engine\":\"MySQL\",\"MasterUserPassword\":\"****\"}", 

            "PhysicalResourceId": "jdzdz5bqeqo7a9", 

            "LogicalResourceId": "DBInstance"

        }, 


…

________________________________________________________________________________

| ~/workspaces/aws @ macmini (james) 

| => aws cloudformation list-stacks

{

    "StackSummaries": [

        {

            "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644", 

            "TemplateDescription": "AWS CloudFormation Sample Template WordPress_Single_Instance_With_RDS: WordPress is web software you can use to create a website or blog. This template installs a single-instance WordPress deployment that uses an Amazon RDS database instance for storage. It demonstrates using the AWS CloudFormation bootstrap scripts to install packages and files when an instance is launched. **WARNING** This template creates an Amazon EC2 instance and an Amazon RDS database instance. You will be billed for the AWS resources used if you create a stack from this template.", 

            "StackStatusReason": "User Initiated", 

            "CreationTime": "2015-03-24T19:37:28.569Z", 

            "StackName": "jsandlinqa1", 

            "StackStatus": "CREATE_IN_PROGRESS"

        }, 

        {

            "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/MyWPTestStack/443a3840-d1a6-11e4-a822-50e2414b0a44", 

            "DeletionTime": "2015-03-23T22:34:36.621Z", 

            "TemplateDescription": "AWS CloudFormation Sample Template WordPress_Single_Instance_With_RDS: WordPress is web software you can use to create a website or blog. This template installs a single-instance WordPress deployment that uses an Amazon RDS database instance for storage. It demonstrates using the AWS CloudFormation bootstrap scripts to install packages and files when an instance is launched. **WARNING** This template creates an Amazon EC2 instance and an Amazon RDS database instance. You will be billed for the AWS resources used if you create a stack from this template.", 

            "StackStatusReason": null, 

            "CreationTime": "2015-03-23T21:47:57.465Z", 

            "StackName": "MyWPTestStack", 

            "StackStatus": "DELETE_COMPLETE"

        }

    ]

}













____________________________________
| ~/workspaces/aws @ macmini (james) 
| => aws cloudformation describe-stacks --stack-name jsandlinqa1
{
    "Stacks": [
        {
            "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/34a75310-d25d-11e4-a5c5-50d50031c644", 
            "Description": "AWS CloudFormation Sample Template WordPress_Single_Instance_With_RDS: WordPress is web software you can use to create a website or blog. This template installs a single-instance WordPress deployment that uses an Amazon RDS database instance for storage. It demonstrates using the AWS CloudFormation bootstrap scripts to install packages and files when an instance is launched. **WARNING** This template creates an Amazon EC2 instance and an Amazon RDS database instance. You will be billed for the AWS resources used if you create a stack from this template.", 
            "Parameters": [
                {
                    "ParameterValue": "****", 
                    "ParameterKey": "DBPassword"
                }, 
                {
                    "ParameterValue": "0.0.0.0/0", 
                    "ParameterKey": "SSHLocation"
                }, 
                {
                    "ParameterValue": "****", 
                    "ParameterKey": "DBUsername"
                }, 
                {
                    "ParameterValue": "db.t1.micro", 
                    "ParameterKey": "DBClass"
                }, 
                {
                    "ParameterValue": "wordpress", 
                    "ParameterKey": "DBName"
                }, 
                {
                    "ParameterValue": "////Users/james/.ssh/aws_keypair_oregon.pem", 
                    "ParameterKey": "KeyName"
                }, 
                {
                    "ParameterValue": "t1.micro", 
                    "ParameterKey": "InstanceType"
                }, 
                {
                    "ParameterValue": "5", 
                    "ParameterKey": "DBAllocatedStorage"
                }
            ], 
            "Tags": [], 
            "StackStatusReason": "The following resource(s) failed to create: [WebServer]. . Rollback requested by user.", 
            "CreationTime": "2015-03-24T19:37:28.569Z", 
            "StackName": "jsandlinqa1", 
            "NotificationARNs": [], 
            "StackStatus": "ROLLBACK_IN_PROGRESS", 
            "DisableRollback": false
        }
    ]
}



| ~/workspaces/aws @ macmini (james) 

| => aws cloudformation delete-stack --stack-name jsandlinqa1







| ~/workspaces/aws @ macmini (james) 
| => aws cloudformation create-stack --template-body file:////Users/james/workspaces/aws/WordPress_Single_Instance_With_RDS.template --stack-name jsandlinqa1
{
    "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/608f60a0-d260-11e4-925a-50d50205787c"
}



________________________________________________________________________________

| ~/workspaces/aws @ macmini (james) 

| => aws cloudformation create-stack --template-body file:////Users/james/workspaces/aws/WordPress_Single_Instance_With_RDS.template --stack-name jsandlinqa1 --parameters ParameterKey=KeyName,ParameterValue=key_pair_oregon

{

    "StackId": "arn:aws:cloudformation:us-west-2:950837372442:stack/jsandlinqa1/3ea36b50-d263-11e4-b600-500160d4da44"

}

aws cloudformation describe-stacks --stack-name jsandlinqa1

_____



