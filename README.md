### Install Update / Packages :
```
sudo apt update -y && sudo apt upgrade -y
```
---
### (OPTIONAL)
### Install screen
```
sudo apt install screen -y
```

### Create screen
```
screen -s `node-name`
```
---

### Run Script
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/monk-io/sonaric-install/main/linux-install-sonaric.sh)"
```

### Confirm that the node is running by issuing the following command
```
sonaric node-info
```
result!
```
 ✨ Node information loaded:
 ├─🧊 ID             12D3XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 ├─📥 Leader         wavy-cream-yacht
 ├─🧊 Version        v1.1.0
 ...
```

### Updating Node
```
apt-get update
```
```
apt-get install sonaricd sonaric
```

### To confirm the node is running the latest version
```
sonaric node-info
```

---
### Accessing the GUI in PC
1. Create an SSH tunnel to forward the required ports to your local machine
Run this on local machine /cli
```
ssh -L 127.0.0.1:44003:127.0.0.1:44003 -L 127.0.0.1:44004:127.0.0.1:44004 -L 127.0.0.1:44005:127.0.0.1:44005 -L 127.0.0.1:44006:127.0.0.1:44006 `user@your-vps-ip`
```

Replace user with your VPS `username` and  `your-vps-ip` with your VPS IP address.

2. You will be prompted to authenticate cia SSH. Once authenticated, the SSH tunnel will be established.
3. Open a web browser on your local machine and navigate to `http://localhost:44004` to access the Sonaric GUI.

### Accessing the GUI in Smartphone

## RECOMMENDED
### Using Termux

1. Install Termux: Download and install the Termux app from the Google Play Store.
2. Open Termux: Launch the Termux app.
3. Update and Install OpenSSH: Update the package list and install the OpenSSH package by running the following commands:
```

pkg update
pkg install openssh
```

4. Create an SSH Tunnel: Use the ssh command to create the tunnel. Replace user, remote_server, and remote_port with your actual details. The command looks like this:

```
ssh -L 127.0.0.1:44003:127.0.0.1:44003 -L 127.0.0.1:44004:127.0.0.1:44004 -L 127.0.0.1:44005:127.0.0.1:44005 -L 127.0.0.1:44006:127.0.0.1:44006 root@'YOUR-IP'
```

`user@remote_server`: Replace user with your SSH username and remote_server with the hostname or IP address of the remote server.

5. Enter Password: If prompted, enter your SSH password to establish the connection.

6. Access the Forwarded Port: Once the SSH tunnel is established, you can access the remote service via 127.0.0.1:44004 or localhost:44004 on your Android device.
    - Use Google Chrome Desktop Mode
  
## On the GUI.
   - click on `Referral Codes` on the upper right corner
   - Add my code provided below for additional 100 points
# troe4jy


-DONE-

---
### Signup Node run
https://docs.google.com/forms/d/e/1FAIpQLSeSeoVwohC4Wu3kZ06FGmKPO5afKKEvwjLresOfSgJjMMO7sA/viewform?fbclid=IwZXh0bgNhZW0CMTEAAR3kbMU6R7EEFV1MFa0beSh4P8E5aWrMa8occAnNV5rN2NxjOVNuZ1CjtJU_aem_JOvv7xwo4awwtiONtapDVg
- preferred name/handle
- discord username
- node id:
```
sonaric node-info
```

- operating system
- System type
- System Specs
- Other nodes RPC: for those who runs other node projects (e.g. allora, rivalz, farcaster, nubit)
- feedback
- Click `Submit`.

---
### Get Operator Role in Discord

1. Open Discord
2. Go to [Sanoric](https://discord.com/invite/k2NGekWtVg) Discord channel.
3. Verify
4. Go to General channel and input command
```
/addnode
```

5. Copy the code provided by sanoric bot
6. Go to local Terminal or GUI (Termux App in Smartphone)
7. Input command :Don't forgot to paste your code from discord!
```
curl -sSL http://get.sonaric.xyz/scripts/register.sh | bash -s -- `your-code`
```
Thank you very much

DONE
