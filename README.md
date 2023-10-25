## Connecting two machines running Ubuntu 22 and Windows 10 on the same network

There are several methods to connect two machines running Ubuntu 22 and Windows 10 on the same network. Here are a few options:

**Using SSH:**

1. On Ubuntu 22, install an SSH server:

    ```
    sudo apt-get install openssh-server
    ```

2. On Windows 10, use an SSH client such as PuTTY to connect to the Ubuntu machine:
    * Enter the IP address of the Ubuntu machine in the "Host Name" field.
    * Select "SSH" as the connection type.
    * Enter your Ubuntu machine's username and password to log in.

**Using Remote Desktop Protocol (RDP):**

1. On Windows 10, enable Remote Desktop:
    * Go to **Settings** > **System** > **Remote Desktop**.
    * Turn on **Enable Remote Desktop**.
    * Make a note of the PC name under **How to connect to this PC**.

2. On Ubuntu 22, install an RDP client such as Remmina:

    ```
    sudo apt-get install remmina
    ```

3. Launch Remmina and create a new connection:
    * Enter the Windows 10 PC's IP address or PC name.
    * Select "RDP" as the protocol.
    * Enter your Windows 10 username and password.

**Using Samba:**

1. On both the Ubuntu and Windows machines, install Samba:

    * On Ubuntu 22:

        ```
        sudo apt-get install samba
        ```

    * On Windows 10: Download and install Samba from the official website.

2. On Ubuntu, create a shared folder:

    ```
    sudo mkdir /home/<your_username>/shared_folder
    sudo chown <your_username>:<your_username> /home/<your_username>/shared_folder
    sudo chmod 777 /home/<your_username>/shared_folder
    ```

    Replace `<your_username>` with your Ubuntu machine's username.

3. On Ubuntu, add the shared folder to Samba's configuration file:

    ```
    sudo nano /etc/samba/smb.conf
    ```

    Add the following lines at the bottom of the file:

    ```
    [shared_folder]
    path = /home/<your_username>/shared_folder
    read only = no
    guest ok = yes
    ```

    Save and exit the file.

4. On Ubuntu, restart Samba:

    ```
    sudo systemctl restart smbd
    

5. On Windows 10, access the shared folder:
    * Open File Explorer.
    * Click "Network" in the left-hand pane.
    * Locate the Ubuntu machine and double-click on it to open it.
    * Double-click on the "shared_folder" to access its contents.

These are just a few ways to connect two machines running Ubuntu 22 and Windows 10 on the same network. The choice of method depends on your specific requirements and preferences.








