# VPN Management Script

This repository contains a script to help you manage your OpenVPN sessions on a Linux system via simple commands. You can import configurations, start, stop, pause, resume, and clean up VPN sessions with ease.

## Prerequisites

Before using this script, make sure you have the following:

- **openvpn3**: This script uses `openvpn3` for managing VPN configurations and sessions. Ensure that it's installed on your system. You can install `openvpn3` by following the instructions on [the OpenVPN Community Wiki and Tracker](https://community.openvpn.net/openvpn/wiki/OpenVPN3Linux).
- **Configuration File**: The script expects a configuration file located in your home directory as a hidden file, specifically `~/.client.ovpn`. Please ensure this file exists and contains the correct configuration for your VPN.

  #### Step 1: Download the Configuration File

  Download your `client.ovpn` file to any location (e.g., the Downloads folder).

  #### Step 2: Move the File to the Hidden Location

  After downloading the file, move it directly to your home directory as a hidden file:

  ```bash
  mv ~/Downloads/client.ovpn ~/.client.ovpn
  ```

  This will move the file to `~/.client.ovpn` and hide it from the default directory listing.

  #### Step 3: Set Proper Permissions

  Set the correct permissions for the file to ensure that it is secure:

  ```bash
  chmod 600 ~/.client.ovpn

  ```

  This will ensure that the file is readable and writable only by you, and not by others on the system.

  #### Security Notice

  While using a hidden file (`~/.client.ovpn`) with restrictive permissions (`chmod 600`) improves security, it is not foolproof. Be aware that applications running under your user account or potential system vulnerabilities could still access the file.

## Installation

### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/basil-r/vpn-management-script.git
```

### Step 2: Place the Script in Your `bin` Folder

To make the script accessible from anywhere in your terminal, place it in the `bin` folder inside your home directory. If the `bin` folder does not exist, you can create it.

1. Open a terminal and navigate to your home directory:

```bash
cd ~
```

2. Create the `bin` folder (if it doesn't already exist):

```bash
mkdir -p ~/bin
```

3. Copy the script to the `bin` folder:

```bash
cp /path/to/downloaded/vpn-management-script/vpn ~/bin/
```

4. Make the script executable:

```bash
chmod 700 ~/bin/vpn
```

This command ensures that only your user can execute the script, and no other users on the system will have access to it.

### Step 3: Update the `PATH` Variable (if needed)

In most Linux systems, the `bin` folder inside the home directory is automatically included in the `PATH` variable. If it's not, you can manually add it to your profile.  
Open your `~/.bashrc` or `~/.profile` file:

```bash
nano ~/.bashrc
```

Add the following line at the end of the file to include your `bin` folder:

```bash
export PATH="$HOME/bin:$PATH"
```

Save the file and apply the changes:

```bash
source ~/.bashrc  # or source ~/.profile
```

### Step 4: Verify the Script is Working

Once you've set up the script, test it by running:

```bash
vpn
```

If everything is set up correctly, you'll see the help message with available options.

## Usage

You can now use the script with simple commands. The general syntax is:

```bash
vpn [OPTION]
```

### Available Options:

- **i**: Import configuration
- **s**: Start VPN session
- **r**: Restart VPN session
- **p**: Pause VPN session
- **e**: Resume VPN session
- **d**: Disconnect VPN session
- **dp** [session-path]: Disconnect VPN session by session path
- **c**: Clean up VPN sessions
- **l**: List VPN sessions
- **h**, **help**: Display help message

### Example Commands

- _Import Configuration:_  
  To import your OpenVPN configuration file (~/.profile.ovpn):

```bash
vpn i
```

- _Start a VPN Session:_  
  To start a new VPN session:

```bash
vpn s
```

- _Close a VPN Session:_  
  To disconnect the VPN session:

```bash
vpn d
```

- _List Current VPN Sessions:_  
  To list the current VPN sessions:

```bash
vpn l
```

- _Disconnect VPN Session by Path:_  
  To disconnect a VPN session by its session path:

```bash
vpn dp [session-path]
```

- _For additional help, run:_

```bash
vpn h
```

## License

This script is licensed under [the MIT License](./LICENSE).
