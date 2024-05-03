![Alt text](/https://github.com/jslearner-app/aws-project-2-deploy-a-static-website/blob/main/Host_a_Static_Website_on_AWS%202.png?raw=true)

# aws-project-2-deploy-a-static-website
aws project 2 deploy a static website on aws
Hosting a Static Website on AWS
Overview
This project demonstrates the deployment of a static HTML web application on Amazon Web Services (AWS) infrastructure. By utilizing various AWS resources and services, the project ensures high availability, security, and scalability of the web application.

Project Components
Virtual Private Cloud (VPC):
Configured a VPC with public and private subnets spanning two availability zones for increased fault tolerance.
Internet Gateway:
Deployed an Internet Gateway to enable connectivity between VPC instances and the internet.
Security Groups:
Established security groups to act as a firewall mechanism, controlling inbound and outbound traffic.
Availability Zones:
Utilized two availability zones to enhance system reliability and fault tolerance.
Public Subnets:
Public subnets were used for resources such as the NAT Gateway and Application Load Balancer.
EC2 Instance Connect Endpoint:
Implemented EC2 Instance Connect Endpoint to establish secure connections to assets within public and private subnets.
Web Servers (EC2 instances):
Deployed web servers (EC2 instances) within private subnets to enhance security.
NAT Gateway:
Enabled instances in private subnets to access the internet via the NAT Gateway.
Website Hosting:
Hosted the static website on EC2 instances.
Application Load Balancer (ALB):
Utilized an ALB and a target group for distributing web traffic evenly to an Auto Scaling Group across multiple availability zones.
Auto Scaling Group:
Utilized an Auto Scaling Group to manage EC2 instances automatically, ensuring high availability, scalability, fault tolerance, and elasticity.
Version Control:
Stored web files on GitHub for version control and collaboration.
Certificate Manager:
Secured application communications using AWS Certificate Manager.
Simple Notification Service (SNS):
Configured SNS to send notifications about activities within the Auto Scaling Group.
Domain Registration:
Registered the domain name and set up DNS records using Amazon Route 53.

Deployment
Refer to the provided scripts and diagrams in the GitHub repository for detailed deployment instructions.

# Switch to the root user to gain full administrative privileges
sudo su

# Update all installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository to the current directory
git clone https://github.com/jslearner-app/aws-project-2-deploy-a-static-website.git

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R aws-project-2-deploy-a-static-website/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf aws-project-2-deploy-a-static-website

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd 

# Start the Apache HTTP Server to serve web content
systemctl start httpd
