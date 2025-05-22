<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This guide explains what you need and how to install the free help desk ticket system called osTicket.<br />




<h2>Environments and Technologies </h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop (RDP)
- Internet Information Services (IIS)

<h2>Operating Systems </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
Welcome to my first detailed IT tutorial!

To start, we’ll create a Virtual Machine (VM) using the Microsoft Azure portal (portal.azure.com). A VM is basically a computer you can use remotely. We're using a VM instead of our own computer to keep our physical machine safe in case something goes wrong, and to have a clean setup we can reuse for this lab.

First, create a resource group and name it "osTicket". Then, create a VM with 2 to 4 CPUs — in this tutorial, I’ll be using 4 CPUs.
  
![image](https://github.com/user-attachments/assets/fe575e13-ec1a-4d2b-85e5-df784cae6832)

</p>
<br />
<p>
</p>
<p>Next, connect to your new VM using RDP (Remote Desktop Protocol) and the public IPv4 address provided.
If you're using a Mac, you’ll need to download the Microsoft Remote Desktop app to make the connection. 
</p>
<img src="https://i.imgur.com/uLVKzxS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
</p>
<p>
Now that you're connected to your VM, you'll need to turn on IIS (Internet Information Services). Here's how:

    Open the Control Panel.

    Click on "Uninstall a program".

    On the left side, click "Turn Windows features on or off".

    A list will pop up — find and check Internet Information Services, then click OK to enable it.
</p>  
<img src="https://i.imgur.com/qtEnuWu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
</p>
<p>
Great! Now that IIS is enabled, the next step is to install the Web Platform Installer.

I’ve provided a link here:
👉 [Download Materials for osTicket Setup](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

Click the link, then download and install the Web Platform Installer from the folder. This tool will help us easily install the other components needed for osTicket.
</p>
<img src="https://i.imgur.com/AxHCfQ6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
Once you've installed the Web Platform Installer, open it.

Inside the app, do the following:

    Install MySQL 5.5.

    Then, install the x86 version of PHP — make sure to go up to version 7.3 (don’t go beyond that).

Some parts may fail to install, like:

    The C++ Redistributable Package

    PHP 7.3.8

    PHP Manager for IIS

Don't worry — these files are included in the download link I shared earlier, so you can install them manually from there if needed.
</p>
<img src="https://i.imgur.com/JJ8bZeJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
Next, download the osTicket software.

Once it’s downloaded:

    Extract the files.

    Open the extracted folder and find the folder named "upload".

    Copy the "upload" folder to this location on your VM:
    C:\inetpub\wwwroot

    After copying it, rename the folder from "upload" to "osTicket".
</P>
<img src="https://i.imgur.com/TUGiSKi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>
Now, follow these steps:

    Open IIS Manager.

    Restart the server from there.

    In IIS Manager, go to Sites → Default → osTicket.

    On the right side, click "Browse *:80".

Your default web browser should now open the osTicket webserver setup page.
</p>
<img src="https://i.imgur.com/4AkTkV0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Here’s what you need to do to enable the extensions:

    Go back into IIS Manager.

    Navigate to Sites → Default → osTicket.

    Double-click on PHP Manager.

    Click on "Disable or enable an extension".

    Enable the following extensions:

        php_intl.dll

        php_opcache.dll

    After enabling the extensions, refresh the osTicket webserver.

Once you’ve done that, you should see that the "Intl Extension" is now enabled.
</p>
<img src="https://i.imgur.com/APZgUTT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Here’s how to configure the ost-config.php file:

    Go to C:\inetpub\wwwroot\osTicket\include.

    Find the file ost-sampleconfig.php and rename it to ost-config.php.

Next, set the correct permissions:

    Right-click on ost-config.php and select Properties.

    Go to the Security tab.

    Click Advanced.

    Click on Disable inheritance and select Remove all inherited permissions from this object.

    Under New permissions, click Add, then select Everyone and grant Full control (All permissions).

Once that’s done, save your changes.
</p>
<img src="https://i.imgur.com/1nYaYGe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Now, continue setting up osTicket in your browser:

    In the osTicket setup page, click Continue to proceed.

    You’ll be asked to name your Helpdesk — choose a name that fits your needs.

    Then, select a default email address where osTicket will receive emails from customers when they submit tickets.

After filling out these details, you can move forward with the rest of the setup process.
</p>
<img src="https://i.imgur.com/RmVk3q5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
<p>Great! Now, let's continue setting up osTicket in the browser:

    For the MySQL Database settings:

        Database Name: osTicket

        MySQL Username: root

        MySQL Password: Password1

    Click "Install Now!".

If everything is set up correctly, you should see a success message with no errors.
Clean Up:

After installation, do the following to secure your setup:

    Delete the setup folder:

        Navigate to C:\inetpub\wwwroot\osTicket\setup and delete the entire folder.

    Set permissions to "Read" only for the ost-config.php file:

        Go to C:\inetpub\wwwroot\osTicket\include\ost-config.php and change the permissions to Read only.

Access the Admin Panel:

Now, you can log in to the osTicket Admin Panel:

    Open your browser and go to:
    http://localhost/osTicket/scp/login.php

Log in with the admin credentials you set up earlier. Congratulations, your osTicket setup is complete!
