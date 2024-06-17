---
title: "How to Set Up a Static Web Server with NGINX? (Step-by-Step Guide)"
seoTitle: "Static Web Server Setup with NGINX"
seoDescription: "Step-by-step guide to set up a static web server with NGINX, including installation, configuration, and deployment tips"
datePublished: Tue Jun 11 2024 21:53:40 GMT+0000 (Coordinated Universal Time)
cuid: clxaxvgpt000209kx8xcrhs56
slug: how-to-set-up-a-static-web-server-with-nginx-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1718132630261/e4ac6587-5909-47fb-9c9f-0915e6146069.png
tags: nginx, install-and-configure-nginx, nginx-project, nginx-installation-tutorial, nginx-server

---

**The first question:***Why we need NGINX when we already have Apache httpd?*  
***Answer:***

While Apache HTTP Server is a powerful and flexible web server, NGINX offers certain advantages that make it a popular choice*(like me😂)* for many use cases:

1. **Performance**: NGINX is known for its high performance, especially under heavy load. It uses an event-driven architecture which allows it to handle thousands of concurrent connections with minimal memory usage.
    
2. **Reverse Proxy and Load Balancing**: NGINX is often used as a reverse proxy and load balancer. This allows it to distribute network traffic across multiple servers to ensure high availability and reliability.
    
3. **Static Content Delivery**: NGINX excels at serving static content quickly and efficiently, making it a great choice for websites with high volumes of static content.
    
4. **Configuration**: Some users find NGINX’s configuration syntax to be more straightforward and easier to read than Apache’s.
    
5. **Microservices Architecture**: NGINX is often used in modern microservices architectures due to its ability to act as a reverse proxy and load balancer.
    

However, this does not make NGINX superior; Apache httpd has been around for a long time and is **Mature and Reliable***(like me😂)*. My preference is:

* * Use Apache httpd when you have a static site like documentation, wikis, etc.
        
    * Use NGINX when using Node.js, Python, or anything that needs port proxying.
        

# Lets Setup NGINX:

*Prerequisites:*

* A basic HTML/CSS/JS web project to deploy.
    
* A Linux machine or server.
    
* Domain name (optional).
    

So, you've mastered web development and created a fantastic webpage. Now, you're eager to share it with the world. But how do you deploy it on the internet? Fear not; I'm here to guide you through the process.

To get started, you'll need a Linux machine or VM. ([**how to create one?**](https://hashnode.com/post/clo3b6ngz000509ld6c76dlv0))

### **Step 0 - Connect to your VM (if using cloud)**

connect to your virtual machine using any of the following ways so we can start installing and configuring apache server on it.  
A. Connect using ssh-

```bash
ssh 192.168.1.7@ashutosh ↩️
yourpassword↩️

This will start a shell session like this:

ashutosh@yourvm:~$
```

B. You can use VNC/RDP. For more information, search for "VNC with your cloud provider term" on Google.

You can skip the above step if you are setting up NGINX on a local server.

### **Step 1 - Update Your Packages 🔄**

First things first, ensure your system is up-to-date by running this command:

```bash
sudo apt update && sudo apt upgrade
```

💡Pro tip: If you're feeling lazy, you can use `sudo su` to avoid typing `sudo` twice!

### **Step 2 - Install NGINX Server 🌐**

Let's get NGINX on board. Run this command:

```bash
sudo apt install nginx
```

Now, technically, NGINX should be installed and running. To test this, let's execute the following command:

```bash
curl localhost
```

This should give the following output:

```bash
bloguser@blogvm:~$ curl localhost

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style></style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>
<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

If you are getting this output, it means NGINX is installed and up and running.

### Step 3 - Enable and Configure firewall🔥🧱

Currently NGINX is running locally, if you try to open the VM's ip in browser it will not show anything, which is obvious as have not enabled `http (80)` and `https(443)` ports from firewall.

What is Firewall again🧱?

A firewall is a security mechanism that protects your VM (aka server) from external connections. The firewall acts as a barrier that only allows access to permitted ports by authorized entities.

When you created a VM, you likely enabled the SSH port (22), knowingly or unknowingly, allowing that port to communicate with your VM. There are several services with associated port numbers that you will need to allow if you want the respective functionality. Below is a list of some popular services and their default port numbers:

| Service | Port Number |
| --- | --- |
| SSH | 22 |
| HTTP | 80 |
| HTTPS | 443 |
| FTP | 21 |
| SFTP | 22 |
| SMTP | 25 |
| MySQL | 3306 |
| PostgreSQL | 5432 |
| MongoDB | 27017 |

*(Please note that these are the default port numbers. They can be configured to use different port numbers based on the requirements. Always ensure that the necessary security measures are in place when opening these ports anywhere.)*

**Back to NGINX:**

As we will be working with web pages, we need to enable `http (80)` and `https (443)`. On Ubuntu systems, `ufw` is used to manage the firewall. We will use this tool.

1. Check if the firewall service is running by running `sudo ufw status`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718136361038/14b2500e-a273-45f7-9bcd-0e062a52274c.png align="center")
    

If the service is not running, start it by running `sudo ufw enable`.

2. Now, enable http, https, and ssh from the firewall.
    

There are multiple ways to do this. The first way is to directly allow ports by name or port number.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718136573583/6cfbc383-60bc-495b-b4be-e1f29662b70e.png align="center")

another way is to check available configurations and enable that way (recommended)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718136639313/214cfbe5-2d66-47b9-b818-2d4eaf2d1c78.png align="center")

3. Finally check status of firewall again by `sudo ufw status` it should look something like this-
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718136517004/d3adbca9-79ad-4927-88dc-34a160a8ce93.png align="center")

Enter your VM's IP in a browser and check if it is showing up. If not, there might be some restrictions from your cloud provider.

For Azure, refer to [this](https://learn.microsoft.com/en-us/answers/questions/1190066/how-can-i-open-a-port-in-azure-so-that-a-constant) guide; for AWS, check [this](https://stackoverflow.com/questions/17161345/how-to-open-a-web-server-port-on-ec2-instance) one; and for DigitalOcean, consult [this](https://www.digitalocean.com/community/questions/opening-ports-in-my-droplet) guide.

You may need to add some policies, as it depends on the cloud provider.

After this, your webpage should show up, which will look something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718137474636/dfd06f06-efc3-41d8-bf5d-be79ae323709.png align="center")

### **Step 4 - Creating Your Website 🌟**

By default, NGINX comes with a basic site enabled. You can customize its content, which is located at `/var/www/html`.

Let's modify the default page with our content.

Step 1 - Navigate to the default directory:

```bash
cd /var/www/html/
ls
sudo rm -r index.nginx-debian.html 
ls
sudo nano index.html
    //if you don't have nano
vim index.html -> i
```

Paste this sample html file-

```bash
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        h1 {
            color: #333;
        }
    </style>
</head>
<body>
    <h1>Hello, World!👋</h1>
</body>
</html>
```

Save and exit

nano -&gt; ctrl+x -&gt; y -&gt; enter.

vim -&gt; :wq -&gt; enter.

Restart the NGINX server

```bash
nginx -t                        //to check the configuratin
sudo systemctl restart nginx    //to restart nginx
```

### Then, refresh your webpage, and it will look something like this:**\-**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718113695292/b8102678-dd8c-49c8-9091-90137f5e7cee.png align="center")

*So this is how you setup a simple static web server with NGINX✨*

## How to Host Your Vanilla JS Projects from GitHub?

Say you have created a simple project on GitHub, and you want to deploy it here. Now, we will see how to do this:

1. For this to work, the `index.html` of your project should be in the root directory. The project structure should look like this:
    

```markdown
.
├── assets
│   ├── logo/logo.png
│   ├── images
│   └── icons
├── index.html
├── style.css
├── index.js
└── README.md
```

2. * Remove the existing files from the `/var/www/html` folder, making sure it's empty. Use the `rm` command to delete files. `sudo rm filename`
        
    * Next, clone the GitHub repository with a `.` path so that all of its contents are directly in this `/html` folder. `git clone yourrepourl .` For example: `git clone`[`https://github.com/ashutosh7i/Yuvaantar_portfolio.git`](https://github.com/ashutosh7i/Yuvaantar_portfolio.git)`.`
        
    * Test the NGINX configuration for syntax errors:
        

```bash
sudo nginx -t
```

7. If the configuration test is successful, reload NGINX to apply the changes:
    

```bash
sudo systemctl reload nginx
```

2. Now, refreshing the IP will show your project. In my case, it looks like this:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718122652297/14e4c138-baa2-4fce-801a-43144654ecce.png align="center")

Here are some additional tips and tricks:

* **Custom project location:** Say you don't always want to use the `/var/www/html` folder. To configure a custom folder location, you can tweak the default config file:
    
    * `nano /etc/nginx/sites-available/default`
        
    * Discard everything and paste this fresh config:
        
    * ```bash
            server {
                    listen 80 default_server;
                    listen [::]:80 default_server;
            
                    root /var/www/html;
            
                    index index.html;
            
                    server_name _;
            
                    location / {
                            try_files $uri $uri/ =404;
                    }
            }
        ```
        
    * replace the `/var/www/html` with the folder of your choice.
        
    * Save the file and restart NGINX.
        
* * 🛠️ **CI pipeline:** Once your project is on the server, you can make changes to it locally, push to GitHub, SSH into the server, and run the `git pull` command to host the latest files.
        
        * 🔒 **Port and Firewall Settings**: If your website is not showing up, ensure that your firewall allows traffic on port 80 (HTTP) and 443 (HTTPS) for your server. You might need to set up these rules using `ufw`, like `sudo ufw allow http`.
            
        * 🏠**Setting Up Server Blocks** Server Blocks in NGINX are similar to Virtual Hosts in Apache. They allow you to host multiple websites/domains on a single server. We will need them when we add SSL and a domain name.
            

### **Getting Familiar with Important NGINX Files and Directories**

* **/etc/nginx**: This is the main directory where NGINX configuration files are stored.
    
* **/etc/nginx/nginx.conf**: The main NGINX configuration file.
    
* **/etc/nginx/sites-available**: Directory where server block configuration files are stored.
    
* **/etc/nginx/sites-enabled**: Directory containing symbolic links to enabled server block configurations.
    
* **/var/log/nginx**: Directory where NGINX log files are stored.
    

### **Server Configuration**

NGINX server configuration is typically done in the `nginx.conf` file located in `/etc/nginx/nginx.conf`. This file contains global settings that apply to the entire NGINX server, such as worker processes, user settings, and error log locations.

### **Server Logs**

NGINX logs important information about server activity, errors, and access in log files located in `/var/log/nginx`. The main log files are:

* **access.log**: Contains records of all requests made to the server.
    
* **error.log**: Logs NGINX errors and warnings.
    

### **Basic NGINX Commands**

* **Start NGINX**: `sudo systemctl start nginx`
    
* **Stop NGINX**: `sudo systemctl stop nginx`
    
* **Restart NGINX**: `sudo systemctl restart nginx`
    
* **Reload NGINX**: `sudo systemctl reload nginx`
    
* **Check NGINX Configuration**: `sudo nginx -t`
    

Now you have a basic understanding of NGINX setup, configuration, and management. 🙌

Stay tuned for the next part where we'll cover SSL installation and domain name configuration! 🔐🌐

That's it! You're on your way to sharing your masterpiece with the world. Stay tuned for more web server wizardry in our upcoming blogs! 🧙‍♂️✨

for any issues you can always reach me out on [**Linkedin**](https://linkedin.com/in/ashutosh7i)

Happy Hacking! ☁️🚀