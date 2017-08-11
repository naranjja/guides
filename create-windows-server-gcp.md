# Windows Server 2016 for Google Cloud Platform
This is a guide for creating a Windows Server 2016 instance on Google Cloud Platform.

* First, visit the [Google Cloud Platform Console](https://console.cloud.google.com).
* Sign in, create an account, then create a project.
* Next, visit the [Compute Engine](https://console.cloud.google.com/compute/) and create a new VM instance.

![Image](/img/create-windows-server-gcp-1.png)

* Set the desired settings and then change the boot disk to **Windows Server 2016**.

![Image](/img/create-windows-server-gcp-2.png)

* Wait for the image to setup, this should take a couple of minutes.

![Image](/img/create-windows-server-gcp-3.png)

* Once ready, select to connect via **RDP**.

![Image](/img/create-windows-server-gcp-4.png)

* A popup window shows up. Select to download the RDP file.

![Image](/img/create-windows-server-gcp-5.png)

* Next, close the popup window and click on the instance's name.

![Image](/img/create-windows-server-gcp-8.png)

* Once inside, select to **Set Windows password**.

![Image](/img/create-windows-server-gcp-9.png)

* Follow the steps of setting up a user and you will get a password. Make sure to copy both the username and password and keep them somewhere safe. Generating a password should not take long. However, sometimes it may hang here. Refresh the page if this happens.

![Image](/img/create-windows-server-gcp-10.png)

* Now we have everything ready to connect. Double-click on the downloaded RDP file.
* Input the username and password you obtained earlier. Do not enable the checkbox that says "Remember my credentials". This causes a known bug on Windows where the connection fails automatically.
