# A High Availability AWS CloudFormation Infrastructure Deployment

An automated deployment of a web application using AWS CloudFormation. This script includes a Virtual Private Cloud on CloudFormation configured with four subnets. A public and private subnet is created in two different availability zones. NAT Gateways are created with Elastic IP addresses so private subnets can communicate with the outside world and remain secure. An application load balancer is configured, autoscaling, security groups and resource access policies are also included.

## Getting Started

Please view the reference architecture diagram and prerequisites before getting started

## Reference Architecture Diagram

![Reference Architecture Diagram](/ReferenceArchitectureDiagram.png)

### Prerequisites

- An [AWS Account](https://aws.amazon.com)
- The [AWS Command Line Interface](https://aws.amazon.com/cli/) for running the Cloudformation script

### Create Cloudformation stack

- Run the creation script from a terminal
  - Using the shell script:
    ```bash
    $ ./create.sh My-Stack-Name infrastructure.yml infrastructure-parameters.json
    ```
  - Directly from the terminal:
    ```bash
    $ aws cloudformation create-stack --stack-name My-Stack-Name --template-body file://infrastructure.yml --parameters file://infrastructure-parameters.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2
    ```

### Update Cloudformation stack

- Run the update script or the update-stack command after modifying the infrastructure YAML file
  - Using the shell script:
    ```bash
    $ ./update.sh My-Stack-Name infrastructure.yml infrastructure-parameters.json
    ```
  - Directly from the terminal:
    ```bash
    $ aws cloudformation update-stack --stack-name My-Stack-Name --template-body file://infrastructure.yml --parameters file://infrastructure-parameters.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2
    ```

### Delete Cloudformation stack

- Run the creation script from a terminal
  - Using the supplied shell script:
    ```bash
    $ ./delete.sh My-Stack-Name
    ```
  - Directly from the terminal:
    ```bash
    $ aws cloudformation delete-stack --stack-name My-Stack-Name
    ```
