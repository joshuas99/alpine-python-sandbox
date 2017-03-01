# alpine-python-sandbox
Quick and easy custom sandbox for running python scripts on py2.7

# How to use the Script Sandbox

## Build Your Container

1. Copy the Dropbox `Dockerfile.zip` to your local machine, any valid folder
2. Unzip the archive in the folder
3. You should see 6 files:

   	authorized_keys
   	script_key.pem
   	Dockerfile
   	home
   	motd
   	README (this file)

Now open a terminal or command prompt in that folder and run the following commands.

	docker build -t <any desired image name> .

This command should take a little time and will generate the container itself with the tagged name. You may use whatever tag you want if you wish to use a different one. The next command will run the container image in Docker.

	docker run -p 2222:22 --name <container name> <image name>
This will start the container and listen on port 2222 for your ssh login. 

## Login to Your Container

To login to the container, use the included `script_key.pem` with your ssh.

> Note that you might have to change the permissions on the key to 600 to make it work. Use `chmod 600 script_key.pem`

	ssh -i script_key.pem -p 2222 sandbox@localhost

> You may also include the key in your `.ssh` directory in your home profile if you wish to skip using the -i.

The `sandbox` user password is `sunshine`.
