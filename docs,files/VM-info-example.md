# VM information for each Cloud Platform
We created a scenario for explanation
```
Source VM : AWS CentOS 7, Azure CentOS 7.6, GCP CentOS 7
Target VM : OCI CentOS 7, OCI CentOS 7, OCI CentOS 7 
```

Follow the *instructions stated below.
(*plain text : follow the instructions, "" : write as it is, [] : name of a file/folder)

## AWS Source VM

- **Profile** : Use default value.
- **Access Key, Secret Access Key, Login Region** : use default value.
    - To use a different login information, enter the Access Key and Secret Access key generated at AWS Cloud Console, and the Region where those keys were generated.
- **Region** : Use default value.
- **OS & OS_version** : "CentOS", "7"
    - To use a different OS and version, select from the toggle list.
- **VM Name** :  Enter the name of the VM in accordance with the constraints.
- **Image** : "ami-09e2a570cb404b37e"
    - To use a different Image, select from the toggle list.
- **Machine Type** : use default value
    - To use a different Machine Type, select from the toggle list.
- **Security Group ID** : Deselect `Automatically create a new security group` and select `sg-073eb02b16e13cb17 (zcon-demo)`
    - To use a different Security Group, you must select from the toggle list which has valid Inbound rules for Migration.
- **Login Key** : [aws_demo_key.pem]
    - To use a different key, use a pem Key generated at AWS Cloud Console
- **Volume** : Use default value
    - To add additional disks, enter the size of the additional disk in accordance with the constraints.
- **User data** : [aws_source_userdata.sh]

&nbsp;
## Azure Source VM

- **Subscription ID** : Use default value
    - To use a different login information, enter the valid Subscription ID
- **Tenant ID & App ID & App PWD** : use default value
    - To use a different login information, enter the Tenant ID, App ID, App password generated at Azure Cloud Console
- **Region** : Use default value
- **VM Name** : Enter the name of the VM in accordance with the constraints.
- **Machine Type & CPU Count & Memory Size** : "Standard_A1_v2"
    - To use a different Machine Type, select from the toggle list.
    - Note : Some Virtual Machines may not be installed properly due to the usage limit of the selected Region. We recommend you to check the usage limit before selecting the machine type or either change the region.
- **OS & OS_version** : "CentOS", "7.6"
    - To use a different OS and version, select from the toggle list.
- **Volume** : Use default value
    - To add additional disks, enter the size of the additional disk in accordance with the constraints.
- **Username & Password** : use default value
    - To use a different username and password, you must create them in accordance with the constraints.
    - Username : Must contain only letters, numbers, hyphens, underscores and cannot begin with hyphens or numbers. Username must not contain reserved words. The value must be between 1 and 64 characters.
        - ex) you can not use "test" as a username 
    - Password : Password must contain 3 of 1 lowercase letter, 1 uppercase letter, 1 number, and 1 special character. The value must be between 12 and 72 characters.
- **User data** : [azure-source-userdata.sh]

&nbsp;
## Azure Source VM

- **Credentionals File** : [gcp_credentials.json]
    - To use a different login information, use the information file generated at GCP Cloud Console
- **Reigon [Zone]** : use default value
- **VM Name** : Enter the name of the VM in accordance with the constraints.
- **Machine Type** : use default value
    - To use a different Machine Type, select from the toggle list.
- **OS & OS_version** : "cent=cloud", "centos-7"
    - To use a different OS and version, select from the toggle list. 
- **User Name** : Enter the name of the VM in accordance with the constraints.
- **SSH Authorized Keys** : [oci_gcp_demo_key.pub]
    - To use a different public key, use a public key that follows public-openssh format 
    - ex) ssh-rsa AAAAB3Nza…… )
- **Volume** : Use default value
    - To add additional disks, enter the size of the additional disk in accordance with the constraints.
- **User data** : [gcp-source-userdata.sh]
- **tags** : "demo"
**firewall_rule** : To generate a new firewall rule, you must enter the tags and the firewall_rules in accordance with the constraints
    - ex) Add firewall rule that allows TCP 4001, 5001 inbound with "test" tag
        - tags : "test"
        - firewall_rule : "tcp:4001,tcp:5001" 



&nbsp;
## Oracle Target VM
- **Credentionals File Upload** : [oci_config]
- **Config Key File** : [oci_config.pem]
    - To use a different login information, use the information file generated at OCI Cloud Console or CLI
- **Compartment Id** : use default value
- **Available Domain** : use default value
- **VM Name** : Enter the name of the VM in accordance with the constraints.
- **Profile** : Use the Profile information stated in the perviously uploaded Config file
    - Example of a Config file
        ```
        [DEFAULT] // ← Profile
        user=*****************
        fingerprint=*****************
        tenancy=*****************
        region=*****************
        key_file=*****************
        ```
- **Machine Type & CPU Count & Memory Size** : use default value
    - To use a different Machine Type, select from the toggle list.
- **OS & OS_version** : "CentOS", "7"
    - To use a different OS and version, select from the toggle list.
- **Subnet** : Deselect `Automatically create a new subnet` and select `subnet-20210421-1418 (ocid1.subnet.oc1.ap-seoul-1.aaaaaaaaikxwifqksivdvnvl27k6mffo7cnvqv4xhw4rvcgjnc7yc7ydkc2q)`
    - To use a different Subnet, you must select from the toggle list which has valid Inbound rules for Migration.
- **Volume** : Use default value
    - To add additional disks, enter the size of the additional disk in accordance with the constraints.
- **Login Key** : [oci_gcp_demo_key.pub]
    - To use a different public key, use a public key that follows RSA format 
- **User data** : [oci_target_userdata.sh]


## Notice / Precautions
A Target VM must contain **minimum 1 additional disk** and **each additional Disk's Size must field must be over 50(GB)**

