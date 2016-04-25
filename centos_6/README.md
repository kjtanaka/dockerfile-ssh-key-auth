# centos6ssh

```bash
docker run -p 2233:22 --name=cn01 -e AUTHORIZED_KEYS="$(cat ~/.ssh/id_rsa.pub)" -dt centos6ssh
ssh -p 2233 -o StrictHostKeyChecking=no -o LogLevel=FATAL -l root localhost
```
