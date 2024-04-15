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

![aptupdate](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/14825858-65a2-4f4d-8b7b-b08ce5606ea4)

```
sudo apt update
```

### Once connected to your EC2 instance via SSH, you'll need to install the Ubuntu Desktop environment. Run the following command

![installubuntuu](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/5a612052-781c-4ec3-9996-323b82fc6652)

```
sudo apt install ubuntu-desktop

```
### For remote desktop access we are going to use TightVNC.

TightVNC is a cross-platform, open-source remote desktop software application. It allows you to view and control a desktop environment remotely over a network connection. TightVNC is based on VNC (Virtual Network Computing), which is a protocol that enables remote access to graphical desktops.To learn more about TightVNC click on this link(https://www.tightvnc.com/)

### Here's how you can set up TightVNC on your Ubuntu EC2 instance..
### type:

![tightvncserver](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/94f7501f-1a88-4619-907c-cc8648e1a13d)

```
sudo apt install tightvncserver

```
### To install several packages associated with the GNOME desktop environment on an Ubuntu system.
### type:

![gnome](https://github.com/kitty6xt5/MINI-PROJECT1/assets/141032592/123012ac-f669-498c-9448-ee3802efb2da)

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

```
vim ~/.vnc/xstartup

```
### Remove all the script inside the file and copy paste the script given below:

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

```
vncserver -kill :1

```

```

vncserver :1

```
### Ensure that the AWS EC2 instance is configured to allow inbound connections using VNC. Access the AWS EC2 console and navigate to the security group associated with your instance. Modify the inbound rules by adding a new entry:
### Match the inbound rules according to the picture given below.

### Now we will Launch Remmina Remote Desktop Client From our Desktop.
Remmina is a popular open-source remote desktop client application for Linux-based operating systems. It allows users to connect to and interact with remote desktops or servers from their local machine.
### Launch Remmina.
### Choose the connection type as ‘VNC’
### Enter your EC2 url along with the number as ```:1```.

For example- If my EC2 Connecting url is ```ec2-52-66-120-136.ap-south-1.compute.amazonaws.com``` then i will use this url with ```:1```

```
ec2-52-66-120-136.ap-south-1.compute.amazonaws.com:1

```

### Now we  have to Enter the password we provided during the installation of the tightVNC Server.

### After Entering the password click on connect...
### Congrats,Our EC2 instance is now set up to run Ubuntu Desktop successfully.
