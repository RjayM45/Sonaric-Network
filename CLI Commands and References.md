# Sonaric CLI Overview
The Sonaric Command Line Interface (CLI) is a powerful tool for managing your Sonaric AI Node and interacting with the Sonaric network. The CLI provides a wide range of commands for configuring your node, monitoring its performance, and interacting with the Sonaric network. You can use the CLI to operate your node from the command line, or integrate it into your own scripts and applications.

Using the CLI is the most efficient way to manage your Sonaric AI Node running on a headless server or VPS.

## Sonaric CLI Commands
Run the `sonaric` command in your terminal to access the Sonaric CLI. The CLI provides a wide range of commands for managing your Sonaric AI Node and interacting with the Sonaric network.

Running the `sonaric` command without any arguments:

```
sonaric
```
displays the following output:

```
NAME:
   sonaric - Sonaric Command Line Interface

USAGE:
   sonaric [GLOBAL OPTIONS] command [OPTIONS] [arguments...]

COMMANDS:
     set-country           Set country location on a peer
     node-info, peer-info  Print info about the current node
     version               Print versions of this CLI and connected daemon
     node-rename           Renaming the node
     help, h               Shows a list of commands or help for one command

   Identity management commands:
     identity-export  Export the current identity(Private Key, Public Key, etc.)
     identity-import  Import the current identity(Private Key, Public Key, etc.)

   Management commands:
     sign  Sign text using private key of node
     gui   Start, upgrade or stop Sonaric GUI

   Workload management commands:
     ps  List running workloads
```

## `set-country` Command
The `set-country` command allows you to set the country location on a peer. This command is useful for specifying the country location of your node. Country will be displayed in the [Sonaric Tracker](https://tracker.sonaric.xyz/) and can be used for filtering nodes by country.

To `set the country` to Japan, run the following command:

```
sonaric set-country -c jp
```
This command accepts country codes like `us`, `ca`, `de`, `jp`, etc.

##  `node-info` Command
The node-info command prints information about the current node. This command displays the following information:

```
✨ Node information loaded:
 ├─🧊 ID             12D3KooXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 ├─📥 Leader         foamy-coral-fish
 ├─🧊 Version        v1.1.0
 ├─🧊 Country
 ├─🧊 Daemon Version v1.1.0
 └─🧩 Host Info
    ├─🧊 OS               darwin
    ├─🧊 Platform         darwin
    ├─🧊 Platform Version 14.3
    └─🧊 Platform Version mmpb.local
```

## `version` Command
The `version` command prints the versions of the Sonaric CLI and the connected daemon. This command displays the following information:

```
CLI version:    v1.1.0, build: 53bc66e4
Daemon version: v1.1.0, build: 53bc66e4
```

## `points` Command
The `points` command prints the points collected by the node. This command displays the following information:
```
✔ Points: 1234
```

## `node-rename` Command
The `node-rename` command allows you to rename your node. This command is useful for changing the name of your node as displayed in the [Sonaric Tracker](https://tracker.sonaric.xyz/).

To rename your node to `my-node`, run the following command:

```
sonaric node-rename -n my-node
```
##  `sign` Command
The `sign` command allows you to sign text using the private key of your node. This command is useful for verifying the authenticity of messages signed by your node. In the future this command will be used for claiming points.

To sign the text `hello`, run the following command:

```
sonaric sign 'hello'
```
The output will be the signed text looking like this:

```
Signed text: F/MCILLUYE6+mWZsblZjmvj7HmlhvoX5p+E1jmueISujCwjre4zKo6KXlqRQ3uygsHXos70wl2luSBZELw5tCA==
```

##  `gui` Command
The `gui` command allows you to start, upgrade, or stop the Sonaric GUI. This command is useful for managing the Sonaric GUI application running on your machine.

Currently the GUI is managed automatically by the Sonaric AI Node, so you don't need to run this command manually.

## `ps` Command
The `ps` command lists the running workloads on your node. This command is useful for monitoring the workloads running on your node and checking their status.

To list the running workloads on your node, run the following command:

```
sonaric ps
```

The output will be a list of running workloads on your node.

```
✔ Got state
Group/Runnable/Containers                                       Ready   Uptime   Peer   Ports
🔩 sonaric/sonaric-gui/latest                                   true
 └─📦 local-04772c682d6043ef286bb69d8d--sonaric-gui-latest-gui          24m 38s  local  44004:8080 44005:44005 44006:44006
```

## `identity-export` Command
The `identity-export` command allows you to export the current identity of your node. This command is useful for backing up your node's identity information.

To export the current identity of your node, run the following command:

```
sonaric identity-export
```

You will be prompted to enter a password to encrypt the exported identity. After entering the password, the identity will be exported to stdout. You can redirect the output to a file or use the `-o` flag to specify the output file like this:

```
sonaric identity-export -o identity.file
```

This will export the identity to `identity.file`. The file should be kept secure and not shared with others. It can be used to import the identity into another node.

## `identity-import` Command
The `identity-import` command allows you to import an identity into your node. This command is useful for restoring a previously exported identity or importing an identity from another node.

To import an identity from `identity.file`, run the following command:

```
sonaric identity-import -i idenity.file
```

You will be prompted to enter the password used to encrypt the exported identity. After entering the password, the identity will be imported into your node.

## Getting Help
To get help with any command, run the `help` command followed by the command name. For example, to get help with the `node-info` command, run:

```
sonaric help node-info
```
