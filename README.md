# Packer for Nginx

Hashicorp Packer is a lightweight, easy to use tool which automates the creation of any type of machine images for multiple platforms. Packer is not a replacement of configuration management tools like Ansible. Packer works with tools like ansible to install software while creating images. Packer uses a configuration file to create a machine image. Packer uses the concepts of builders to spin up an instance, run provisioners to configure applications or services. Once setup is done, it shuts the instance down and save new baked machine instance with any needed post-processing. Packer only builds images.
