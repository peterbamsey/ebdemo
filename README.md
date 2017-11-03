# ebdemo - Elastic Beanstalk demo 
Demo for deploying a static website to AWS using Elastic Beanstalk

## Dependencies
- An AWS account with programmatic access, including AWS access key and secret key
- [>=EB CLI 3.12.0](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)
- [>=aws-cli/1.4.2](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

## How to deploy
Once the above dependencies are met, ensure you have configured your AWS credentials file.  The easiest way to do this is to create the file ~/.aws/config with the contents:

>[default]  
>region = eu-west-1  
>aws_secret_access_key = [YourSecretAccessKey]  
>aws_access_key_id = [YourSecretAccessKeyID]  

Then clone the project:
> git clone [url]
From within the project directory initialise the project with the following command and answers the questions when prompted:
> eb init
>Select a default region
>1) us-east-1 : US East (N. Virginia)
>2) us-west-1 : US West (N. California)
>3) us-west-2 : US West (Oregon)
>4) eu-west-1 : EU (Ireland)
>5) eu-central-1 : EU (Frankfurt)
>6) ap-south-1 : Asia Pacific (Mumbai)
>7) ap-southeast-1 : Asia Pacific (Singapore)
>8) ap-southeast-2 : Asia Pacific (Sydney)
>9) ap-northeast-1 : Asia Pacific (Tokyo)
>10) ap-northeast-2 : Asia Pacific (Seoul)
>11) sa-east-1 : South America (Sao Paulo)
>12) cn-north-1 : China (Beijing)
>13) us-east-2 : US East (Ohio)
>14) ca-central-1 : Canada (Central)
>15) eu-west-2 : EU (London)  
>
>(default is 3): 4  
>
>Select an application to use
>1) ebdemo
>2) [ Create new Application ]
>
>(default is 1): 1  
>
>It appears you are using PHP. Is this correct?
>
>(Y/n): Y
>
>Select a platform version.
>1) PHP 5.4
>2) PHP 5.5
>3) PHP 5.6
>4) PHP 7.0
>5) PHP 7.1
>6) PHP 5.3
>
>(default is 1): 5
>Note: Elastic Beanstalk now supports AWS CodeCommit; a fully-managed source control service. To learn more, see Docs: https://aws.amazon.com/codecommit/
>Do you wish to continue with CodeCommit? (y/N) (default is n): n
>Do you want to set up SSH for your instances?
>(Y/n): n

Then to create and deploy the project: (Accept defaults where possible)
>eb create
>Enter Environment Name
>(default is ebdemo-dev): 
>Enter DNS CNAME prefix
>(default is ebdemo-dev): 
>
>Select a load balancer type
>1) classic
>2) application
>3) network
>
>(default is 1): 1
>
>Creating application version archive "app-9ff5-171103_134854".  
>...  
>  CNAME: ebdemo-dev.eu-west-1.elasticbeanstalk.com  
>  Updated: 2017-11-03 13:47:59.941000+00:00  
>
>INFO: Successfully launched environment: ebdemo-dev  

The above may take several minutes to complete.  Once done the project will be available at the URL output above:
> CNAME: ebdemo-dev.eu-west-1.elasticbeanstalk.com

## Updating the page
Once you have the project cloned locally, make any required changes to index.html, commit them locally and run eb deploy to push updates to your site:
>eb deploy
