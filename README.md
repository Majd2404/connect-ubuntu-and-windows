# To connect two machines running Ubuntu 22 and Windows 10 that are on the same network, you can use several methods. Here are a few options

+ Using SSH:
On Ubuntu 22, you can install an SSH server, and on Windows 10, you can use an SSH client such as PuTTY to connect to the Ubuntu machine. First, you need to enable SSH on the Ubuntu machine by running the following command in the terminal:

  $ sudo apt-get install openssh-server

Once the installation is complete, you can find the IP address of the Ubuntu machine by running the following command:

  $ ip addr show

Then, on Windows 10, you can use PuTTY to connect to the Ubuntu machine by entering the IP address in the "Host Name" field and selecting "SSH" as the connection type. You can then enter your Ubuntu machine's username and password to log in.

+ Using Remote Desktop Protocol (RDP):
On Windows 10, you can enable Remote Desktop, and on Ubuntu 22, you can install an RDP client such as Remmina. First, you need to enable Remote Desktop on the Windows 10 machine by following these steps:

Go to "Settings" > "System" > "Remote Desktop."
  + Turn on "Enable Remote Desktop."
  + Make a note of the PC name under "How to connect to this PC."
  + Next, you can install Remmina on Ubuntu 22 by running the following command in the terminal:
  
  $ sudo apt-get install remmina

Once Remmina is installed, you can launch it and create a new connection by entering the Windows 10 PC's IP address or PC name, selecting "RDP" as the protocol, and entering your Windows 10 username and password.

+ Using Samba:
Samba is a file-sharing protocol that allows Windows and Linux machines to share files and printers. To use Samba, you need to install it on both the Ubuntu and Windows machines. On Ubuntu 22, you can install Samba by running the following command in the terminal:

  $ sudo apt-get install samba

Once Samba is installed, you can create a shared folder on Ubuntu by running the following commands:

  $ sudo mkdir /home/<your_username>/shared_folder
  $ sudo chown <your_username>:<your_username> /home/<your_username>/shared_folder
  $ sudo chmod 777 /home/<your_username>/shared_folder
  
Replace <your_username> with your Ubuntu machine's username. You can then add the shared folder to Samba's configuration file by running the following command:  
  $ sudo nano /etc/samba/smb.conf

Add the following lines at the bottom of the file:

[shared_folder]
path = /home/<your_username>/shared_folder
read only = no
guest ok = yes

Save and exit the file, and then restart Samba by running the following command:

  $ sudo systemctl restart smbd


On Windows 10, you can access the shared folder by opening File Explorer, clicking "Network" in the left-hand pane, and locating the Ubuntu machine. Double-click on the Ubuntu machine to open it, and then double-click on the "shared_folder" to access its contents.

These are some ways to connect two machines running Ubuntu 22 and Windows 10 that are on the same network. The choice of method depends on your specific requirements and preferences.






