# dockerfiles

This is a collection of Dockerfiles that allow SSH Key Authentication.

## Download Dockerfiles

```bash
$ git clone https://github.com/kjtanaka/dockerfile-ssh-key-auth.git
$ cd dockerfile-ssh-key-auth
```

## Example Ubuntu 14.04

```bash
# Create Ubuntu 14.04 image
docker build -t ubuntu1404ssh ubuntu1404ssh

# Create a container
docker run -p 2233:22 --name=cn01 -e AUTHORIZED_KEYS="$(cat ~/.ssh/id_rsa.pub)" -dt ubuntu1404ssh

# Log in to the container
ssh -p 2233 -l root localhost

# If you want to disable StrictHostKeyChecking, add "-o StrictHostKeyChecking=no"
# and "-o LogLevel=FATAL" like this.
ssh -p 2233 -o StrictHostKeyChecking=no -o LogLevel=FATAL -l root localhost
```
