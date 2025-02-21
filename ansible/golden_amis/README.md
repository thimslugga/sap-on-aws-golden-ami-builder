# sap-golden-ami
Ansible code for SAP Golden AMI build - RedHat and OEL

Code covering:
- Installing packages
- Installing AWS SAP data provider
- Install EFS driver
- Installing SSM
- Installing AWS CLI
- Enable NFS
- Set clocksource
- Setting /etc/sysctl.d/sap.conf
- Setting timezone
- Set tuned
- Set UUIDD
- Creating groups
- Creating users
- For OEL specific: Everything from here https://oracle-base.com/articles/19c/oracle-db-19c-installation-on-oracle-linux-8 until "Additional Setup"

## Userdata for the instance

```
ansible_playbook_folder="/home/ec2-user/sap-golden-ami"
rm -rf $ansible_playbook_folder

sudo yum install -y git ansible-core
git clone https://github.com/aws-samples/aws-sap-golden-ami-image-builder $ansible_playbook_folder
sudo ansible-playbook $ansible_playbook_folder/ansible/golden_amis/bootstrap_instance.yaml
```