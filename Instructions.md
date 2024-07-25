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
1. To create an SSH tunnel to forward the required ports to your local machine
2. Install Termius_App: Download and install the Termius app from Google Play Store.
3. Open Termius: Launch the Termius App
4. Add Host: *Set Up `SSH Connection`*:
    - Tap the `+` button to create a new host.
    - Enter the necessary SSH connection details:
        - *Label*: Give the connection a name (e.g., "My Server/Sonaric").
        - *Hostname*: Enter the hostname or IP address of the remote server.
        - *Port*: Usually 22 (default for SSH).
        - *Username*: Your SSH username. (contabo uses `root` as default username)
        - *Password*: Your SSH password (or leave blank if using key-based authentication).

4. *Set Up Port Forwarding*:
    - After saving the host, tap on it to open the details page.
    - Tap on `Port Forwarding`.
    - Tap the `+` button to add a new port forward.
    - Configure the port forwarding:
        - *Type*: Choose `Local` for local port forwarding.
        - *Source Port*: The port on your Android device you want to forward (e.g., `44004`).
        - *Destination*: The destination in the format `localhost:remote_port` (e.g., `localhost:22` for forwarding to `port 22` on the remote server).
    - Save the port forwarding settings.

5. *Connect to the SSH Server*:
    - Go back to the host details and tap "Connect".
    - Enter your SSH password if prompted or use your private key if set up.

6. *Access the Forwarded Port*: Once the SSH tunnel is established, you can access the remote service via `127.0.0.1:44004` or `localhost:44004` on your Android device.

### Example Configuration

Let's say you want to forward `local port 44004` on your Android device to `port 22` on the remote server:

1. *Host Configuration*:
    - *Label*: My Server
    - *Hostname*: remote_server_ip (e.g., 192.168.1.100)
    - *Port*: 22
    - *Username*: your_username
    - *Password*: your_password (if not using keys)

2. *Port Forwarding Configuration*:
    - *Type*: Local
    - *Source Port*: 44004
    - *Destination*: localhost:22

Following these steps will create an SSH tunnel and forward `local port 44004` on your Android device to port 22 on the remote server using Termius.

-DONE-

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
