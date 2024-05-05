# aws
aws testing and examples


### List
AWS Tasks to practice more: 
1. Create an windows EC2 machine in private subnet which will have access to the internet but not the other way around. (Hint, use NAT Gateway) 
- Then on this machine install with choco something to see how to manage the NAT gateway properly to allow certain connections. 

(VPC peering and Kubernetes Installation with kubeadm and containers creation and publishing apps and accessing them from the other Windows server. )
2. Install 2 linux servers in a public subnet in a different VPC , create a Kubernetes cluster with them . One worker the other is a master. 

3. create an ec2 linux machine and encrypt its volume with a certificate from AWS KMS. 
- Do the same for windows machine too.
- Create a snapshot out of the encrypted EBS disks and then from the snapshots create an unencrypted volumes in a different AZ. Then create from them a different linux and windows machines.  

4. Create a RAID of disks for an instance of EC2. (This task is not relevant because the RAID is configured from the Operating System. And not via AWS. )

5. Create a fully automatic snapshot/ backup of a ebs volume (Hint use Data Lifecycle Manager service)

6. Create a 2 ECS cluster one using Fargate and another using EC2 instances. Note the pricing differs between these two ways. Next Create the Task Definition files for the containers and start them. What containers ? the app that we will create shortly in the beginning of the workshop. which will have static files and a simple webapp. 

(I think that we can create an app that counts the amount of times we click on the screen in python and html and css. with chatgpt and with blackbox to learn what blackbox is... ) 
Important that in this excercise we will practice on IAM role/policy which will allow or deny permissions of the Container Tasks to AWS Services. 

7. Create an EC2 instance and add to it a IAM role policy which blocks the CLOUDWATCH from getting metrics about this instance.

8. Use ALB to manage network connections to 2 ec2 instances which are simple web servers. Note using ALB costs money because we are going to use an Elastic IP which costs money. So as you finish with the excersice remove the IP and then the ALB or the other way around. 

9. Create 2 ec2 instances and use kubeadm to install a master server on one and the other as its worker and have a working k8s cluster. For testing that its working, deploy on the worker machine an application like nginx and see that its working using curl. 

10. install prometheus and grafana and create a basic dashboard in grafana about metrics from where/what prometheus is taking metrics. try on the k8s cluster created in the previous excercise. If not you can try on a third ec2 server which will have just prometheus and grafana and we can use "stress" command line to create spikes which will be recorded in prometheus and then will be presented in the grafana dashboard.

11. Create a simple script not endless application which we will upload to lambda and we will execute it. 
- create a lambda function which triggered by uploading a file to s3, the lambda function will have a role set to it with a policy which allows the lambda to get and create buckets and upload objects from one bucket to another. It will be a backup lambda which will create another bucket with the name backup and it will have the same content. if the backup bucket already exists it will just make sure everything exists. no need for recursion we can make it a flat folder and it will be enough for study buckets and lambdas. 
- we will add to it a SNS usage to send me an email when the lambda is triggered and a new object is created. 

12. we will simulate SQS usage with 2 apps one is sending messages the other is getting them. 
We will purposly slow down the app that gets the messages in order to show how they fail to catch all data sent.
We then will add to the architecture the SQS in order to slow down the amount of messages that are sent to the apps that get the messages. We will not have a load balancer in here it will be a single server in each side to save cost on the ALB and Elastic IP address. 

Note: I can take the calculator app which is shown in lesson 181 in the course and use it as a reciever and we will only need to create an app which will send messages to it. 

13. Create a session web server with chatgpt or blackbox ai. which will do the following:
The server will have two locations , login which will create a session with a token by the name of the client which is entered as value. then it will be saved in a redis/memcache db then the user will be forwarded to the page where he will be available to press a button and see how many times it clicked on it. The server will be a python server. the main thing here is to have an application which uses a memory cache database. and then we can experiment with saving sessions inside the database for practice. Note DynamoDB is also supporting cache maybe we can also use it for the architecture. 

14. IoT Project demo for clients once I feel ready I can try to work on this. I thought about using Alexa as an Iot which can even process lambda functions to do something for example tell what the weather is going to be. 
Or another idea I have which is to connect to a cheap which will be connected to a simple electrical circuit with a light bolt which is going to be turned off or its not working or even that the cable of the circuit is cut and the cheap should send us updates about these life changes. via AWS IoT services. 

15. make sure to learn to the max and even try to test the following services : VPN and Direct Connect to on-premise datacenter of clients. In order to know how to use these services because our clients are using these mostly. 

16. know migration tools and transfer data from on-premise /cloud to AWS because this is the other thing we do mostly for our clients. 

17. AI practice can be the same as presented in the course in lesson 283.
Which is upload image to s3 , which will trigger a lambda function execution which will trigger to AWS Rekognition which will return to the lambda function another trigger which will create in a dynamoDB an item which will list what we see in the image.


Note: need to think about more excersices which relate to storage and network: 
- backups/ snapshots and encryption, with different types of EBS/FS /S3 
- ELB including - NLB or ALB with DNS , direction to destination rules by request to the ELB

The example static html can be seen in lesson 146. 

When I will finish with this course, I want to go over it again and create excersices from each section so I will have good practice until I will start working and will have the exam. 