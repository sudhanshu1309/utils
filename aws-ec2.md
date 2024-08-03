### Create a New User
```bash
sudo adduser newusername
```

### Create the .ssh Directory for the New User
```bash
sudo mkdir /home/newusername/.ssh
sudo chown newusername:newusername /home/newusername/.ssh
sudo chmod 700 /home/newusername/.ssh
```

### Create the authorized_keys File and Add the Public Key
```bash
sudo echo "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEHKFdW+mjfZgbjFJWXtcdF73ZSxKhphHS1IaCKsIN6P newusername@domain.com" | sudo tee /home/newusername/.ssh/authorized_keys
sudo chown newusername:newusername /home/newusername/.ssh/authorized_keys
sudo chmod 600 /home/newusername/.ssh/authorized_keys
```

### Set the Correct Permissions
```bash
sudo chmod 700 /home/newusername/.ssh
sudo chmod 600 /home/newusername/.ssh/authorized_keys
```

### Add the New User to the sudo Group
```bash
sudo usermod -aG sudo newusername
```

### Configure SSH Daemon (if necessary)
```bash
sudo vi /etc/ssh/sshd_config
```

### Test the New User's SSH Access
```bash
ssh -i /path/to/newuser_private_key newusername@your-ec2-instance-public-ip
```
