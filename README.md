Installing Sonaric AI Node on VPS
The installation process is similar to installing Sonaric AI Node on a Linux machine, but without the GUI application. You will need to run the node in headless mode and manage it using the command line.

Installing Sonaric AI Node on a Virtual Private Server (VPS) is discouraged as it is intended to run on personal machines. However, if you still wish to proceed, follow the steps below.

IMPORTANT

When running on a VPS it is your responsibility to set up a firewall and secure your server. Sonaric AI Node does not provide out-of-box security features for VPS instances.

Read the Security section to learn more about securing your node.

Moreover, you will need to manually update the node when new versions are released in order to keep the node up-to-date at all times.

Read the Updating section to learn more about updating your node.

Before you proceed please note that Sonaric AI Node is primarily intended to run on personal machines and not on VPS instances.

System Requirements
Before installing Sonaric AI Node on your VPS, ensure your machine meets the following requirements:

Minimal	Recommended
4 GB RAM	8 GB+ RAM
2 CPU cores	4+ CPU cores
20 GB free disk space	100 GB+ free disk space (SSD)
amd64 CPU Architecture	amd64 CPU Architecture
Installing on VPS
To install Sonaric AI Node on your VPS, follow these steps:

Create a VPS instance with the specified system requirements.

SSH into your VPS instance.

Run the following command to download and execute the installation script:

bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/monk-io/sonaric-install/main/linux-install-sonaric.sh)"
The script will install Sonaric and its dependencies. This process may take a few minutes.

Once the installation is complete, sonaricd will be started automatically.

Confirm that the node is running by issuing the following command:

bash
sonaric node-info
It should return the node information if the node is running:


 ✨ Node information loaded:
 ├─🧊 ID             12D3XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 ├─📥 Leader         wavy-cream-yacht
 ├─🧊 Version        v1.1.0
 ...
See the CLI Overview to learn more about the Sonaric CLI and its features.

Updating
To update Sonaric to the latest version, simply use the package manager to update the sonaric package:

bash
apt-get update
apt-get install sonaricd sonaric
If you are running the node on a different distribution, you can still use the package manager to update the node. Refer to your distribution's documentation for more information.

You can also re-run the installation script.

To confirm the node is running the latest version, issue the following command:

bash
sonaric node-info
Security
When running Sonaric AI Node on a VPS, it is your responsibility to secure your server against unauthorized access, data breaches, and other security threats. Sonaric AI Node does not provide out-of-box security features for VPS instances and Sonaric team is not responsible for securing your server.

Firewall
Set up a firewall to restrict access to your server. If your VPS provider does not offer security groups or firewall setting in their dashboard you can use ufw or iptables to configure the firewall rules.

Recommended firewall rules:

Port	Protocol	Description	Action
44003	TCP	Sonaric API	Deny incoming traffic
44004	TCP	Sonaric API	Deny incoming traffic
44005	TCP	Sonaric GUI	Deny incoming traffic
44006	TCP	Sonaric P2P	Deny incoming traffic
These are the default ports used by Sonaric AI Node. They should not be exposed to the public internet.

In order to access the Sonaric API, GUI, or P2P network, you can use SSH tunneling or a VPN to connect to your server securely.

See Accessing the GUI for more information on how to access the GUI securely when running on a VPS.

SSH
Disable root login and password authentication for SSH. Use SSH keys for authentication and create a new user with sudo privileges.

Ensure that the SSH port is not exposed to the public internet and use a non-standard port for SSH to prevent brute-force attacks.

Keep your SSH keys secure and do not share them with others.

Accessing the GUI
TIP

This step is optional. Only do this if you want to access the Sonaric GUI running on your VPS. Accessing the GUI is not required to run the node.

To access the Sonaric GUI running on your VPS, you can use SSH tunneling to securely connect to the GUI from your local machine.

Create an SSH tunnel to forward the required ports to your local machine by issuing the following command on your local machine:

bash
ssh -L 127.0.0.1:44003:127.0.0.1:44003 -L 127.0.0.1:44004:127.0.0.1:44004 -L 127.0.0.1:44005:127.0.0.1:44005 -L 127.0.0.1:44006:127.0.0.1:44006 user@your-vps-ip
Replace user with your VPS username and your-vps-ip with your VPS IP address.

TIP

Make sure not to run this command on your VPS. Run this command on your local machine to establish an SSH tunnel to your VPS. If you are using Windows, you can run this command in WSL or use PuTTY to create an SSH tunnel using ports specified above.

You will be prompted to authenticate cia SSH. Once authenticated, the SSH tunnel will be established.

Open a web browser on your local machine and navigate to http://localhost:44004 to access the Sonaric GUI.

You can now interact with the Sonaric GUI securely from your local machine.

You will need to keep the SSH tunnel open to access the GUI. If you close the SSH connection, the GUI will no longer be accessible and you will need to re-establish the SSH tunnel to access it again using the same command.

Backup and Recovery
Identity Backup
Each Sonaric AI Node has a unique identity that is used to identify the node on the network. The identity is generated when the node is first started and is used to sign messages and participate in the network. Points are awarded to the node based on its identity. If you lose your node's identity, you will lose all the points associated with that identity.

It is recommended to back up your node's identity when running on a VPS to prevent data loss in case of hardware failure or other issues.

Exporting Identity
In case you want to retain your node's identity, you can use the sonaric identity-export command to export your identity to a file. You can then import it on a new node using the sonaric identity-import command.

This is useful when you want to transfer your node's identity to a new server without copying the entire node data.

In order to export the current identity of your node to a file called your-node-name.identity, run the following command:

bash
sonaric identity-export -o your-node-name.identity
TIP

You can specify a different file name by changing your-node-name.identity to the desired file name. The name is arbitrary and can be anything you like.

You will be prompted to enter a password to encrypt the exported identity. After entering the password, the identity will be exported to the specified file.

You should save the identity file in a secure location and do not share it with others. It contains sensitive information that can be used to impersonate your node. Make sure to remember the specified password as you will need it to import the identity on a new node.

TIP

It is normal to see different file contents each time you export the identity. The file is encrypted using a method that randomizes the output.

Importing Identity
To import the identity on a new node from a file called your-node-name.identity, use the sonaric identity-import command:

bash
sonaric identity-import -i your-node-name.identity
You will be prompted to enter the password used to encrypt the exported identity. After entering the password, the identity will be imported into your new node.

See the Sonaric CLI Reference for more information.

IMPORTANT

NEVER import a single identity file on multiple nodes. There is no need to share identities between nodes. Sharing identity might result in your node being disqualified from the network.

Full Backup
It is recommended to back up your node's data regularly to prevent data loss in case of hardware failure or other issues.

To back up your node's data, simply copy the /var/lib/sonaricd (and ~/.sonaric if exists) directory to a secure location. This directory contains all the data related to your node, including the node identity, database, configuration files, and logs.

To restore your node from a backup, simply copy the backed-up directory to the same location on the new server while sonaricd service is stopped and start the sonaricd service.

IMPORTANT

Do not share your backup files with others or store them in an insecure location. Keep your backups secure to prevent unauthorized access to your node's data and identity# Nodes
