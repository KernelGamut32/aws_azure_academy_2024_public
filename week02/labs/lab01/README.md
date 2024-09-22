# Lab 01 - [AWS - n-Tier Deployment Using IaC](https://medium.com/@lucywachiye/deploying-a-3-tier-architecture-web-application-using-aws-cloudformation-f15974f5620f)

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
1. In the provided terminal from the `~/environment` folder, clone the project repository using `git clone https://github.com/wachiyel/Skillsync_CloudFormation.git`
1. Review the contents of the provided CloudFormation template (BrinveMotors_3_tier_app.yml)
1. Note the 2 references to a key called `Brinve_key` on lines 272 and 293 of the template; this is a reference to a public/private key pair in AWS that will be used to securely connect to the EC2 instances for automatic configuration
1. Create a new key pair called `Brinve_key` using the following instructions (optionally, you can use a different name for your key pair - you'll just need to update lines 272 and 293 in the template before pushing it to AWS):
    - In a separate tab, search for "Key pairs" and open
    - Click "Create key pair"
    - Give the key pair a name, leave type at "RSA", and change file format to ".pem"
    - Click "Create key pair"
    - This will download the public key to your local system to use if/when you want to connect to the web server EC2 instances
    - If you want to connect to the web server EC2 instances, change `CidrIp` on line 224 to your machine's IP address before deploying (leave the `/32` in place as this is used by CIDR to identify a single IP)
    - **NOTE:** Cloud9 does not automatically save changes to files - if a file shows a "white circle" in its tab, you have unsaved changes that need to be persisted
1. Push the CloudFormation template to AWS using `aws cloudformation create-stack --stack-name ntier --template-body file://./Skillsync_CloudFormation/BrinveMotors_3_tier_app.yml`
1. **NOTE:** It may take several minutes (10 - 15) for the deployment to complete
1. You can watch the progress of your CloudFormation deployment using 1 of the 2 following methods:
    - Run `aws cloudformation describe-stack-events --stack-name ntier` to view the status of the stack creation (**use `q` to free up the terminal display**)
    - In `CloudFormation` in the Management Console, you can also watch the progress of your updates
1. Once the deployment is complete, review the "Outputs" tab of the "ntier" CloudFormation stack
1. Find the "WebLoadBalancerDNSName" output value from the CloudFormation stack - click the provided link to launch the simple landing page for the application
1. Find the "AppLoadBalancerDNSName" output value from the CloudFormation stack - click the provided link to attempt to launch the back-end; this will fail as it is configured for private (internal) access only
