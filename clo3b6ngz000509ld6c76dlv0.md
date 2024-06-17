---
title: "How to Create a Virtual Machine in Azure"
datePublished: Mon Oct 23 2023 19:46:46 GMT+0000 (Coordinated Universal Time)
cuid: clo3b6ngz000509ld6c76dlv0
slug: how-to-create-a-virtual-machine-in-azure
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698089579819/8a7f1547-fa30-44a3-a589-0868cc10dac7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698090352933/54da5da0-c3be-4a74-89bc-642ff2188428.png
tags: virtual-machine, azure, web-development, cloud-computing

---

This guide provides step-by-step instructions on how to create a virtual machine in Azure. It covers all the necessary details, from navigating the Azure portal to configuring the virtual machine settings. Following this guide will allow someone to easily create a virtual machine in Azure for their specific needs.

## Step by Step instructions-

1. After registration navigate to [https://portal.azure.com/](https://portal.azure.com/)
    
2. Click on Create a new Resource.
    
    (any "entity" or service is a resource in Azure, for ex a VM is a resource, a Database will be a resource, a domain name is a resource etc)
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698082911719/e7ff0f92-3156-4077-bf14-61356b6dcc37.png align="center")
    
    Search or select "Virtual Machine"
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698082944134/b6e2456c-f9c6-4283-9945-09e18e346079.png align="center")
    
    Click on "Create" to create a VM.
    
5. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698082982817/f3ccdd0d-4254-4075-a316-7daab72986d1.png align="center")
    
    Select your subscription (appears by default)
    
6. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083003987/79c38607-18ae-40a6-acb0-81dd7b80fdea.png align="center")
    
    Create a new Resource Group, let's call it "testResource"
    
    (a resource group as the name signifies is a group of resources combined to deploy an application for ex- a vm+database+ip+domain together make ashutosh7i.dev, so they can be put together in ashutosh7iResource group for easier management)
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083040524/27c7af10-299c-4fc7-9977-b5adfef77a73.png align="center")
    
    Enter the Virtual Machine Name, I name it "testVM"
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083104734/e1b7d89c-eac5-4d0e-ad29-54d7b26d0b9f.png align="center")
    
    You can choose other Availability options and zones, (i'll choose East Asia)
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083156207/05087cdd-91e6-490b-8424-ab2cc15f954a.png align="center")
    
    Here comes the main part, Select your preferred linux distro, for this tutorial we will go with Ubuntu.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083190316/2bd7a1da-a703-418c-8531-a5e16c82a239.png align="center")
    
    Select vm size, for a simple vm, we wont need higher resources, so lets choose the cheapest.
    
11. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083247964/f50e4125-ef8e-4f88-9ff2-82193692ece8.png align="center")
    
    Now we have to set Authentication type or say how would we connect to our vm after deployment,
    
    for a new machine there are two ways-
    
    1\. [Cloud shell](https://azure.microsoft.com/en-in/get-started/azure-portal/cloud-shell/?ef_id=_k_CjwKCAjws9ipBhB1EiwAccEi1L0aqBIH-wEbyKwSEvgEXyIAFqUiMw753_AFrqsLdSHG4uLmA3jF4RoCWocQAvD_BwE_k_&OCID=AIDcmmf1elj9v5_SEM__k_CjwKCAjws9ipBhB1EiwAccEi1L0aqBIH-wEbyKwSEvgEXyIAFqUiMw753_AFrqsLdSHG4uLmA3jF4RoCWocQAvD_BwE_k_&gclid=CjwKCAjws9ipBhB1EiwAccEi1L0aqBIH-wEbyKwSEvgEXyIAFqUiMw753_AFrqsLdSHG4uLmA3jF4RoCWocQAvD_BwE), a shell inside browser, used for emergency cases.  
    2\. [SSH](https://www.cloudflare.com/en-in/learning/access-management/what-is-ssh/), the recommended way.
    
    In SSH there are two methods, we will go with 2nd method that uses much simpler username and password to connect to our vm.
    
12. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083534555/43b639bd-a260-4b1c-aa98-0a15d4c0973d.png align="center")
    
    Enter username and Password. (write down or copy somewhere too)
    
13. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083570743/f275d4aa-c529-4121-8330-5467a532f68e.png align="center")
    
    Click "Allow selected ports" and select HTTP, HTTPS & SSH ports, this will save us time during connection web server installation.
    
14. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083659246/1065ea2d-0c65-4c30-99cc-62ae4ce9762e.png align="center")
    
    Click "Next : Disks &gt;" (now most of the configuration should be left as it is)
    
15. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083685171/0ba918dc-6e69-472a-b38b-4632a7d4f2d0.png align="center")
    
    Click "Next : Networking &gt;"
    
16. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083714424/f4e789d5-e271-4a28-8db6-b22502fb7081.png align="center")
    
    Click "Next : Management &gt;"
    
17. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083732443/41fb7083-3207-4bb1-a670-cd3611a80708.png align="center")
    
    Disable Auto-Shutdown, Click "Next: Monitoring&gt;".
    
18. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083748680/efb13556-01f3-464f-9c19-3d99e785f84b.png align="center")
    
    Click "Next : Tags &gt;"
    
19. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083784746/0d8aed03-f4fb-412c-986f-b180b02cfb8c.png align="center")
    
    Click "Next : Review + create &gt;"
    
20. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698083806242/314caf9b-3f07-432f-996a-00f36a90542e.png align="center")
    
    Here you can verify your resources and hourly cost
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698089740128/4dca2473-b8e0-4d76-ae27-2a1c2b393219.png align="center")
    
21. Click Create when upon verifying details.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698089864314/9890e8f7-93e1-4d54-8106-90765aa676ba.png align="center")
    
22. After some time your deployment will be complete, go to Resource.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698089960492/26da4fc3-54f5-4a41-b9b0-a33ddecb0fbe.png align="center")
    
23. Congratulations your VM is deployed successfully.🎉🎉
    
    ok now how to connect?
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698090107645/0831fb75-7387-4d82-87fc-cc2b9749131f.png align="center")
    
    *Now, let's learn how to connect to your new VM:*
    
24. To Connect use this IP , username and your password.
    
    1. Open any shell.
        
    2. Enter command-
        
        ```bash
        ssh username@serverIp  {press enter}
        password:  {enter password} {press enter}
        ```
        
    3. Example-
        
        On Windows, press Win+R, type "cmd," and press Enter. Then, enter the command as above.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698084726534/c0fcec44-4e31-45fe-a37a-c1f4adc2e52a.png align="center")
        
25. Now, you have the power of Linux at your fingertips. Try out some Linux commands and explore your new virtual machine! 🐧💻
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698084838981/be162c4a-d32e-405c-a1a3-3b036deae924.png align="center")
    
    ## **Summary:**
    
    In this step-by-step guide, you've learned how to create a virtual machine in Azure, from signing up and configuring settings to connecting to your new VM. Now it's time to explore your virtual machine.
    
    for any issues you can always reach me out on [Linkedin](https://linkedin.com/in/ashutosh7i)
    
    Happy Hacking! ☁️🚀