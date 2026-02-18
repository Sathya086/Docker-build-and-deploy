# Docker-build-and-deploy
Docker build and deploy python application using Jenkings CI/CD Pipeline
===========================================
Installed docker and jenkins, java in AWS ec2 (ubuntu)

-----------

Docker installation :
https://docs.docker.com/engine/install/ubuntu/

-----------

Java and Jenkins installation :
https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

-----------

After all above installation, run below commond :
root@ip-172-31-44-110:/home/ubuntu# sudo usermod -aG docker jenkins
root@ip-172-31-44-110:/home/ubuntu# sudo systemctl restart jenkins
root@ip-172-31-44-110:/home/ubuntu# sudo chmod 666 /var/run/docker.sock

-----------

Initiate to run jenkins automation script (jenkins automation script to build and deploy container), while pushing content in github, need to set webhooks in github :

1) Navigate to the “Settings” tab in GitHub Project
2) Select the “Webhooks” option on the left menu
	Click “Add Webhook”
		For “Payload URL”:
			Use the address for the Jenkins server instance (e.g. http://ip:8080)
			Add /github-webhook/ to the end of it.
			Note: Make sure to include the last /!
			example: http://ip:8080/github-webhook/
3) Select “application/json” as the encoding type
4) Leave “Secret” blank (unless a secret has been created and configured in the Jenkins “Configure System -> GitHub plugin” section)
5) Select “Let me select individual events”
		Enable PUSH event
		Enable Pull Request event
6) Make sure “Active” is checked
7) Click “Add Webhook”

-------------

in your Jenkins Job
Build Triggers: select "GitHub hook trigger for GITScm polling"

===========================================

Outputs:



<img width="1817" height="962" alt="docker-deploy-project-1" src="https://github.com/user-attachments/assets/9c6cd55b-c05f-4be2-8235-de7feea36cfa" />

<img width="1847" height="962" alt="pushed to github, started automation -docker-deploy-project-1" src="https://github.com/user-attachments/assets/dec88a6c-b34e-4155-9f27-a5e7234f012b" />

<img width="1828" height="958" alt="jenkins pipeline was succesful-docker-deploy-project-1" src="https://github.com/user-attachments/assets/ae307b01-f42a-4719-b4d1-b3ad8e9a21ca" />

<img width="1813" height="771" alt="container created succefully on server-docker-deploy-project-1" src="https://github.com/user-attachments/assets/c37006c4-bd63-4c56-a1d6-cea81f89ea59" />

<img width="1852" height="915" alt="for ec2pulicip3000 content is loading" src="https://github.com/user-attachments/assets/de1b5b96-4858-4fb2-b1ce-9e2cf38ca20e" />
