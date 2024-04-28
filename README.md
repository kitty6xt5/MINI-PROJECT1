# MINI-PROJECT1

![main](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/5d074550-800c-4528-b27c-614a57e185a9)

## In this project, we are going to use the Ubuntu CLI terminal to connect to an Ubuntu Desktop environment running on an AWS EC2 instance.

### First of all we have to launch an instance using ubuntu AMI.

![launchinstancee](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/953821e3-ab53-4abc-b60b-0fcb30f1a992)

### Launch the instance and connect it through ssh on terminal.

![ssh](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/5b976161-1bea-40d9-97da-b70145abfc20)

```
ssh -i "your key" ubuntu@(your publicip).compute-1.amazonaws.com
```

### After connecting the instance, type -

![aptupdate](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/ff85edd5-fca1-4a72-bc01-8b3b38252c5a)

```
sudo apt update
```

### Once connected to your EC2 instance via SSH, you'll need to install the Ubuntu Desktop environment. Run the following command

![installubuntuu](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/7609db58-25ca-45a5-ade7-5d28ed370932)

```
sudo apt install ubuntu-desktop

```
### For remote desktop access we are going to use TightVNC.

TightVNC is a cross-platform, open-source remote desktop software application. It allows you to view and control a desktop environment remotely over a network connection. TightVNC is based on VNC (Virtual Network Computing), which is a protocol that enables remote access to graphical desktops.To learn more about TightVNC click on this link(https://www.tightvnc.com/)

### Here's how you can set up TightVNC on your Ubuntu EC2 instance..
### type:

![tightvncserver](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/f4547c2e-2467-4abf-a14f-5f6ff02811e2)

```
sudo apt install tightvncserver

```
### To install several packages associated with the GNOME desktop environment on an Ubuntu system.
### type:

![gnome](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/8a0811d7-569f-475e-ba20-7f33317e9e85)

```
 sudo apt install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal

```

### Start TightVNC Server:

![vnceserver1](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/ff668041-30a0-4d8a-9aab-d8e057a21af8)

```

vncserver :1

```
 This command will prompt you to set a password for VNC access. Enter and confirm your desired password.

### IT will ask you to enter read only password type ```n``` for it.

### Create a VNC Configuration File :

Create a configuration file to define the session properties. Create a file named ```.vnc/xstartup``` in the home directory of the user running the VNC server:

### open the configuration file in vim:

![xstartup](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/30147f2e-7e43-4c95-af2b-228522cd63c1)

```
vim ~/.vnc/xstartup

```
### Remove all the script inside the file and copy paste the script given below:

![filescript](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/5ec93f51-38e6-4572-b2e6-54ed6f8d3170)


```
#!/bin/sh

export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey

vncconfig -iconic &
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &

```

### Now,Restart the VNC server by killing it first and then starting it up.
### type:

![vncserverkill](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/e188e75a-8fea-4b6e-8191-6abdfaf82736)

```
vncserver -kill :1

```

```

vncserver :1

```
### Ensure that the AWS EC2 instance is configured to allow inbound connections using VNC. Access the AWS EC2 console and navigate to the security group associated with your instance. Modify the inbound rules by adding a new entry:
### Match the inbound rules according to the picture given below.

![inboundd](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/18f820cf-b017-47f1-9262-3bf4e1a40d60)

### Now we will Launch Remmina Remote Desktop Client From our Desktop.

![remmina](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/5ac5456d-1162-43a5-912b-933c0bdba888)

Remmina is a popular open-source remote desktop client application for Linux-based operating systems. It allows users to connect to and interact with remote desktops or servers from their local machine.
### Launch Remmina.
### Choose the connection type as ```VNC```

![vnc](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/8e387e63-f036-4a28-9f87-c6f914d4e229)


### Enter your EC2 url along with the number as ```:1```.

For example- If my EC2 Connecting url is ```ec2-52-66-120-136.ap-south-1.compute.amazonaws.com``` then i will use this url with ```:1```

```
ec2-52-66-120-136.ap-south-1.compute.amazonaws.com:1

```

### Now we  have to Enter the password we provided during the installation of the tightVNC Server.

![entervncpasswd](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/127d29af-e1c3-41db-b8d1-19a30e2ecb8d

### After Entering the password click on connect...

![desktop](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/369aeab4-ab61-4527-8afb-b2e85f7a9fce)

### Congrats,Our EC2 instance is now set up to run Ubuntu Desktop successfully.
