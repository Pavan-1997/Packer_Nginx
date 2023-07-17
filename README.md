# Packer

- Hashicorp Packer is a lightweight, easy-to-use tool which automates the creation of any type of machine images for multiple platforms. 
- Packer is not a replacement for configuration management tools like Ansible. 
- Packer works with tools like Ansible to install software while creating images. 
- Packer uses a configuration file to create a machine image. Packer uses the concepts of builders to spin up an instance and run provisioners to configure applications or services.
- Once setup is done, it shuts the instance down and saves a new baked machine instance with any needed post-processing. 
- Packer only builds images.

Advantages:

```
- Fast infrastructure deployment: Machine images allow us to launch provisioned and configured machines faster.

- Scalable: Packer install and configure all software for a machine during image creation time, so we don’t need to run any configuration management tool. With same AMI we can spawn any number of instances without doing extra configuration.

- Multi-provider support: Packer can be used to create images for multiple cloud providers like AWS, GCP, Digital Ocean etc.

- Provides testability: Machine images can be tested to verify that they are working.
```

Disadvantages:

```
- Manageability: No AMI manageability is provided by packer. You need to manage them yourself using tags or versions. Keep deleting old unused AMIs.
```

![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/fdda7a2c-2af1-4c11-9f9c-a6d7b7937f9b)

1. Declare all the required VM configurations in an HCL (Hashicorp configuration language) or a JSON file. Let’s call it the Packer template.

2. To build the VM image, execute Packer with the Packer template..

3. Packer authenticates the remote cloud provider and launches a server. If you execute Packer from a cloud environment, it leverages the cloud service account for authentication.

4. Packer takes a remote connection to the server (SSH or Winrm).

5. Then it configures the server based on the provisioner you specified in the Packer template (Shell script, Ansible, Chef, etc).

6. Registers the AMI

7. Deletes the running instance


Packer is template-driven, templates are written in JSON format or HCL and the template is divided into 3 sections:
```
- Variables: Custom variables that can be overridden during runtime by using the -var flag.

- Locals: It is scoped within the Packer template. If you want to pass any sensitive information in a variable, you can convert it to a local value and then mark it as sensitive. This way, the value won’t be printed anywhere in the Packer build logs.

- Source: It is used to define the source of the machine image you want to build. It specifies the type of source (e.g., AWS, VirtualBox, Docker, etc.) and the specific configuration for that source.

- Builders: You can specify multiple builders depending on the target platforms (EC2, VMware, Google Cloud, Docker …).

- Provisioners: You can pass a shell script or use configuration management tools like Ansible, Chef, Puppet or Salt to provision the AMI and install all required packages and software

- Post-Processor: This is not a mandatory block. In this block, we can specify what to do after creating the Image. For example, you can execute a local shell script to create a file with all the image details.
```
---
# Deploying Nginx AMI using Packer

1. Install the Packer on your system and set the path for the environment variable.


2. User the below command int the terminal to check the packer version and to confirm if it is installed
```
packer --version
```


3. Initialize the packer
``` 
packer init main.pkr.hcl
```


4. Validate the packer
```
packer validate main.pkr.hcl
```

5. Build the packer file
```
packer build -var "aws_access_key=<Your-Key>" -var "aws_secret_key=<Your-Key>" main.pkr.hcl
```
You can see the EC2 instance is created temporarily:
![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/9af0f118-dfc4-4f02-a0f9-5670833ac885)


You can see the EC2 instance is stopped after executing the provisioner and creating an AMI:
![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/33db140f-efdb-4efa-bec6-8a2802ad5090)

![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/7f4b49f0-3da2-4c37-a2dd-716ed89ff0aa)


AMI that is created:
![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/86dcf381-6988-445c-9d59-cbfa40082137)

6. Now create an EC2 Instance from the AMI and access the Nginx 

![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/a40cd52f-4927-4192-a60e-fe363c55eec0)

