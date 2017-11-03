# ebdemo - Elastic Beanstalk demo 
Demo for deploying a static website to AWS using Elastic Beanstalk

## Dependencies
- An AWS account with programmatic access, including AWS access key and secret key
- [>=EB CLI 3.12.0](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)
- [>=aws-cli/1.4.2](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

## How to deploy
Once the above dependencies are met, ensure you have configured your AWS credentials file.  The easiest way to do this is to create the file ~/.aws/config with the contents:

**[default]**  
**region = eu-west-1**  
**aws_secret_access_key = [YourSecretAccessKey]**  
**aws_access_key_id = [YourSecretAccessKeyID]**  

Then clone the project:  

**git clone https://github.com/peterbamsey/ebdemo.git**  

From within the project directory:  

**eb init -r eu-west-1 -p PHP7.1**  
**eb create -r eu-west-1 -p PHP7.1 --elb-type classic -c myebtest myebtest**  
**Creating application version archive "app-9ff5-171103_134854".**  
**...**  
**CNAME: myebtest.eu-west-1.elasticbeanstalk.com**  
**Updated: 2017-11-03 13:47:59.941000+00:00**  
**...**  
**INFO: Successfully launched environment: myebtest**  

The above may take several minutes to complete.  Once done the project will be available at the URL output above:  

**CNAME: myebtest.eu-west-1.elasticbeanstalk.com**  

## How to scale
You can scale the project horizontally by increasing the number of instances running the project:  

**eb scale 2**  

Would increase the number of Elastic Beanstalk instances.  

To scale vertically you can set the instance size during project creation by including the -i [instancetype] switch:  

**eb create -r eu-west-1 -p PHP7.1 --elb-type classic -c myebtest -i t2.small myebtest**  

## Updating the page
Once you have the project cloned locally, make any required changes to index.html, commit them locally and run eb deploy to push updates to your site:

**eb deploy**  
