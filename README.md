# Packer for Nginx

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
Manageability: No AMI manageability is provided by packer. You need to manage them yourself using tags or versions. Keep deleting old unused AMIs.
```

![image](https://github.com/Pavan-1997/Packer_Nginx/assets/32020205/fdda7a2c-2af1-4c11-9f9c-a6d7b7937f9b)

1. Declare all the required VM configurations in an HCL (Hashicorp configuration language) or a JSON file. Let’s call it the Packer template.

2. To build the VM image, execute Packer with the Packer template..

3. Packer authenticates the remote cloud provider and launches a server. If you execute Packer from a cloud environment, it leverages the cloud service account for authentication.

4. Packer takes a remote connection to the server (SSH or Winrm).

5. Then it configures the server based on the provisioner you specified in the Packer template (Shell script, Ansible, Chef, etc).

6. Registers the AMI

7. Deletes the running instance
