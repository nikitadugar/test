# EBDeployment Through Jenkins

For code deployment in ElasticBeanstalk we follow the following steps

- firstly we added a plugin in jenkins.
  [AWS Elastic Beanstalk Deployment Plugin](https://wiki.jenkins.io/display/JENKINS/AWSEB+Deployment+Plugin)

- In credential management section add a credential for Bit-bucket or any other resource where is your repository and second credentials of AWS account.

- After adding crerdentials we start to create a free style job.

- Configure git repository in source code management. Reference image:
  
  <p align="center"><img src="https://user-images.githubusercontent.com/50652676/67359542-12697c00-f581-11e9-932d-b21fd5e699da.png" /></p>
  
- Add a build step with "AWS Elastic Beanstalk" and configure it with proper details.

  <p align="center"><img src="https://user-images.githubusercontent.com/50652676/67360300-18f8f300-f583-11e9-8395-af89635a6506.png" /></p>
