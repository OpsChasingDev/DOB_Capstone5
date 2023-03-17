# DOB_Capston5
Integrating Ansible with Jenkins pipeline

## Requirements
- Dedicated Jenkins server
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