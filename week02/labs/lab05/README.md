# Lab 05 - [AWS - CloudWatch Dashboards](https://github.com/aws-samples/aws-cdk-lambda-cloudwatch-dashboard)

1. Login to your A Cloud Guru account
1. Click the "Playground" icon at the top of the page
1. Click the "Start AWS Sandbox" button
1. Login to the AWS Sandbox using the provided instructions and credentials
1. In the AWS Sandbox, create a new Cloud9 environment using the following steps:
    - Open `CloudShell` (in the upper right)
    - Clone this repository to `CloudShell` using `git clone https://github.com/KernelGamut32/aws_azure_academy_2024_public.git`
    - Navigate to the root folder using `cd aws_azure_academy_2024_public`
    - Execute the bash script to create a new Cloud9 environment using `./cloud9.sh '<env-name>' 't3.medium' 'amazonlinux-2023-x86_64' <sleep-time>` (replace `<env-name>` with your environment name and `<sleep-time>` with the targeted delay)
    - Close `CloudShell`
    - In the search bar, search for `Cloud9` (open in a new tab)
    - Click the radio button next to your environment and click `Open in Cloud9`
    - Execute the remaining instructions in the Cloud9 environment
1. In the provided terminal from the `~/environment` folder, clone the project repository using `git clone https://github.com/KernelGamut32/cloudwatch-lambda-dashboard.git`
1. Navigate to the target folder using `cd cloudwatch-lambda-dashboard`; feel free to explore the contents of the provided CDK files
1. With this CDK project, we are going to use `projen` to help us manage configuration and execution of our app (https://aws.amazon.com/blogs/devops/getting-started-with-projen-and-aws-cdk/)
1. Run `npm install` to install the required dependencies
1. Run `npx projen` to incorporate and confirm any configuration updates
1. Run `npx cdk bootstrap` in the terminal to bootstrap the CDK environment
1. Run `npx projen build` to build the application, synthesize the CloudFormation template, and run the tests & linter for the project to validate
1. Run `npx projen deploy` to deploy the CDK stack
1. When deploy completes, you can verify the presence of the Lambdas, API Gateway, and CloudWatch dashboard
1. Try running a few test requests through the API Gateway endpoints (use the "prod" endpoint) using combinations of the following; you can safely run this same set of requests multiple times as there is no actual back-end persisting the data:
    - `curl -X POST -d '{"transaction_id": 1234, "name": "Widget"}' <API Gateway URL>/transactions`
    - `curl <API Gateway URL>/transactions/1234`
    - `curl -X PUT -d '{"transaction_id": 1234, "name": "Widget Update"}' <API Gateway URL>/transactions/1234`
1. Navigate to CloudWatch in the AWS MC and click "Dashboards" to see the activity displayed on the dashboard widgets
1. Run `npx projen destroy` from the project folder to delete the AWS resources for the lab
