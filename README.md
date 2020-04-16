# Static

This project is the part of Cloud DevOps Nanodegree program in which I need to setup a CI/CD pipeline using Jenkins to push the static website code to AWS S3 bucket and host the static website through S3 bucket.

## Creating Network Stack

For creating the network, run the network.yaml template with parameters file network.json

1. Create a network setup by running the below command.

    ```shell
    aws cloudformation create-stack --stack-name <stack_name> --parameters file://network.json --template-body file://network.yaml
    ```

2. Delete the stack by running the below command.

    ```shell
    aws cloudformation delete-stack --stack-name <stack_name>
    ```


## Creating Application Stack

For hosting the static website using S3 bucket, run the `server.yaml` template with parameters file `server.json`

1. Create a server setup by running the below command.

    ```shell
    aws cloudformation create-stack --stack-name <stack_name> --parameters file://server.json --template-body file://server.yaml --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM
    ```

2. Delete the stack by running the below command.

    ```shell
    aws cloudformation delete-stack --stack-name <stack_name>
    ```

### Components

* [x] VPC
* [x] 1 Public Subnets
* [x] Internet Gatway
* [x] Route table for public subnet with asssociation.
* [x] S3 bucket
* [x] t2.micro instance to setup Jenkins
* [x] Group attached with `AmazonEC2FullAccess, AmazonVPCFullAccess, AmazonS3FullAccess` policies
* [x] User added to the above Group

### Jenkins Pipeline (CI/CD)

1. Lint HTML

    It will check for the linting of the HTML code.

2. Upload to AWS

    It will upload the static files to S3 bucket post the linting stage if passed.
