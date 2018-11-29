# pulumi-handson
If you are here, you belive that you can code you infrastructure using your favorite programming language.
During this journey, 

![alt text](architecture_lambda.png "Transcoder Architecture")

We will convert our RSS to MP3 and saved it to S3

So let's get started :blush:

## First Step : Prepare the field

For this hand-on you need to install node version 8.9
you can use node version manager to handle multiple node version

the installation instruction are available here: https://github.com/creationix/nvm

To check you install: `nvm --version`

Now you can install node 8.9.4 using : `nvm i 8.9.4`

To check you node default version: `node --version`

You can use `nvm use 8.9.4` to switch node version

To Install pulumi you can copy and paste this command in your terminal : `curl -fsSL https://get.pulumi.com | sh`

To check you pulumi version: `pulumi version`

## Second Step : Prepare the weapon

Now you can checkout the projet and start coding :cloud:

- In th main route of the project you have to run `npm i` to install the pulumi depencencies
- you need also to define your Pulumi stack  `pulumi stack init` : you can call your stack `stack
- you need to set francfort as aws region `pulumi config set aws:region eu-central-1`

## Third Step : Fight

### Create the Rss reader function

This function read every day the aws rssFeed and save the last feeds on dynamoDB

The function code is availaible on the package rs-reader

1. Create the RssReaderRole:
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/iam/#Role
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/iam/#RolePolicy
   Your function should be able to to acces to cloudwatch and dynamoDB
2. Create your function with the created role
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/lambda/#Function
3. Create DynamoDB table:
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/dynamodb/#Table
4. Add the the table name to the function enviromenent Variable  
4. Create scheduled event to launch the function periodcally
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/cloudwatch/#EventRule
5. Connect the scheduled event to your lambda function
   https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/cloudwatch/#EventRuleEventSubscription
6. Don't forget to export all created variable
7. launch `pulumi up` to deploy your function

You should test your function: connect to the aws console and select lambda service

In your lambda function, you can test it using the test functonality available on the aws console

you don't need to specify any event or data, just save the test and click on test to trigger your lambda function.

You can select DynamoDB service and check if you have the last aws articles

### Create the audio transcoder function

1. Create the S3 bucket:
    https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/s3/#Bucket
2. Create the AudioTranscoderRole
   Your function should be able to to acces to cloudwatch, dynamoDB,polly and s3
3. Create your function with the created role
4. Create a connect the dynamoDB stream to the AudioTrancoder function
    the function will be triggred when new item is added to the table
    https://pulumi.io/reference/pkg/nodejs/@pulumi/aws/dynamodb/#TableEventSubscription
4. Add the the bucket name to the AudiTranscoder function enviromenent variable  
5. launch `pulumi up` to update your stack





