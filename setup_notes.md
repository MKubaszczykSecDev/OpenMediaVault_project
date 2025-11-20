This section covers everything done after installing OMV and logging in into the OMV web interface for the first time

1) Initial Login:
    Logged into the OMV web interface (http://<PI_IP_ADDRESS>) using default admin credentials which are 
    username: admin
    Password: openmediavault
    The default credentials can be changed for increased security:
    Profile icon in the top right corner > change password.

2) Secure User Creation:
    Created a secure, dedicated NAS user (secureuser). This user can only access the NAS via file explorer, cannot control the server. By setting the Shell to /bin/nologin, this option prevents unauthorized SSH access.

    1) On the left, head to Users
    2) Click Users again and you should see your personalised admin account, to add a guest user (secureuser), click the pencil
    to create a new user.
    3) Enter a name, password, set shell to /bin/nologin, and check "Disallow account modification", click save.
    4) Apply "pending configuration changes" on the top of the screen


3) Disk Preparation:
    On the left side plane, find storage.
    1) Verified external drive detection in Storage > Disks. 
    2) Click the desired Disk and click the rubber icon to wipe the drive to ensure a clean partition table.    
    3) Once the disk is wiped, make your way to back to storage > File Systems.
    4) Click the plus icon and select the recommended Ext4 filesystem, select your wiped disk and click Mount.
    5) After it finishes loading, on the same filesystems screen, click the play ">" icon, select your disk and mount again.
    6) Apply "pending configuration changes" on the top of the screen

4) Shared Folder Setup: 
    On the left side plane, find storage > Shared Folders.
    1) Clicked on the plus icon, named the folder "MiniNAS"
    2) Selected the disk from "Disk Preperation" stage and selected permissions. I kept mine default for now.
    3) Clicked Save and went back to Users > Users > secureuser > clicked the folder icon > assigned R/W permissions.
    4) Save and Apply "pending configuration changes" on the top of the screen.

5) SMB/CIFS Configuration:
    On the left side plane, find services > SMB/CIFS > settings. 
    1) Enabled the SMB/CIFS service. (Here you can see various settings, configure as you wish, though mine will stay default for now.) Click save.
    2) Secure Share Deployment: In SMB/CIFS > Shares: I Configured the SMB/CIFS share: 
    3) Ensure its enabled and select your disk.
    4) Set Public: No (enforcing password authentication)
    5) Enabled Transport encryption to secure all file data traveling across the network.
    6) Save and Apply "pending configuration changes" on the top of the screen.

6) Connection Test:
    Tested the connection from Windows File Explorer

    1) Open file explorer
    2) On the left side, head down to Network
    3) Windows might tell you to turn on File sharing and Network discovery. Turn it on by clicking on the notification
    4) The name of your PI will pop up, double click and enter the credentials for user created earlier (Mine is superuser)
    5) Name of the shared folder will appear (as long as you followed the instructions) and double click to open
    6) Now i have access to my own NAS, using just a Raspberry PI.