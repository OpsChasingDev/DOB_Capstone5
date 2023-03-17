# DOB_Capston5
Integrating Ansible with Jenkins pipeline

## Requirements
- Dedicated Jenkins server
  - Make sure SSH Agent plugin is installed (this is used for copying necessary files to Ansible control node)
  - SSH Key to allow Jenkins server to talk to Ansible server: create credential with "SSH username with private key" type; username will be "root", and private key will be the one used to access the Ansible and Jenkins servers on whatever platform they are running on.
  - If private key is in new type, convert it using the below:
    ```Bash
    ssh-keygen -p -f .ssh/id_rsa -m pem -P "" -N ""
    ```
  - SSH Key to allow Ansible server to talk to EC2 server: create credential with "SSH username with private key" type; username will be "ec2-user", and private key will be the pem file contents created when the ec2 instances were made.
- Dedicated Ansible control node server
  - Install Ansible
    ```Bash
    apt install ansible
    ```
  - Install pip3
    ```Bash
    apt install python3-pip
    ```
  - Ensure Python3 is installed
  - Install boto3 and botocore
    ```Bash
    pip3 install boto3 botocore
    ```
  - AWS Credentials
    - Make .aws directory in root user home
      ```Bash
      mkdir .aws
      ```
    - Make credentials file in new directory
      ```Bash
      cd .aws/
      vim credentials
      ```
    - Paste content in new file from same file on local machine
- In this project, the ec2 instance are created manually.  When doing so, create a new key-pair; download this as it will be used by Ansible server to connect to ec2 instances