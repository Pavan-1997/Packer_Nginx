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
