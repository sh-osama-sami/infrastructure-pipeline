# Infrastructure Pipeline Setup with Terraform and Jenkins

## Description
This project aims to set up an infrastructure pipeline using Terraform and Jenkins. The pipeline will provision AWS resources using Terraform and configure application EC2 instances using Ansible. Additionally, it will configure Jenkins slaves on EC2 instances and deploy a Node.js application using a Jenkins pipeline. The application will be exposed through an Application Load Balancer.

## Steps

1. **Create Infrastructure Pipeline with Jenkins and Terraform:**
   - Install Jenkins on a server (e.g., AWS EC2 instance).
   - Install Terraform on the Jenkins server.
   - Configure Jenkins credentials to access AWS.
   - Create a new Jenkins pipeline job.
   - In the pipeline job, define the pipeline script to fetch the Terraform code from your repository and execute Terraform commands (init, plan, apply).

2. **Create Ansible Script for EC2 Configuration:**
   - Install Ansible on the Jenkins server.
   - Write an Ansible playbook to configure application EC2 instances.
   - Include tasks such as installing dependencies (e.g., Node.js), deploying application code, configuring web servers, etc.

3. **Configure Ansible for Private IP Access via Bastion Host:**
   - Edit the `~/.ssh/config` file on the Jenkins server.
   - Define SSH connection settings for accessing private EC2 instances through a bastion host.

4. **Configure EC2 Instances as Jenkins Slaves:**
   - Write an Ansible playbook to configure EC2 instances as Jenkins slaves.
   - Install Jenkins agent software on EC2 instances.
   - Configure EC2 instances to connect to the Jenkins master.

5. **Configure Jenkins Slave in Dashboard:**
   - Access Jenkins dashboard.
   - Navigate to Manage Jenkins > Manage Nodes and Clouds.
   - Click on "New Node" to add a new slave node.
   - Provide necessary configurations including labels, remote root directory, and launch method (e.g., via SSH).
   - Specify private IP address for connecting to the slave node.

6. **Create Pipeline to Deploy Node.js Application:**
   - Write a Jenkins pipeline script (Jenkinsfile) to deploy the Node.js application.
   - Define stages for checking out source code, building application, running tests, deploying to EC2 instances, etc.

7. **Add Application Load Balancer to Terraform Code:**
   - Edit the Terraform code to include an Application Load Balancer resource.
   - Configure listener, target group, and health checks for the load balancer.
   - Associate EC2 instances running the Node.js application with the target group.

8. **Test Application:**
   - Access the Application Load Balancer URL in a web browser.
   - Verify that the application is accessible and functional.
   - Test the `/db` and `/redis` endpoints to ensure proper integration with RDS and Redis databases.

9. **Create Documentation with Screenshots:**
   - Capture screenshots of each step in the process.
   - Write detailed documentation explaining each configuration and deployment step.
   - Organize the documentation in a clear and understandable format.

10. **Deploy Jenkins on EKS with Dynamic Jobs:**
    - Set up an EKS cluster on AWS using `eksctl`.
    - Deploy Jenkins on the EKS cluster using Helm charts (`helm install jenkins stable/jenkins`).
    - Install Kubernetes plugin on Jenkins.
    - Configure Jenkins to dynamically provision build agents using Kubernetes pods.
    - Define Jenkins jobs to execute pipeline steps on dynamically provisioned Kubernetes agents.


