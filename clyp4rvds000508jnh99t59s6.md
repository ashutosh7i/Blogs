---
title: "How to Deploy a React application with NGINX?"
seoTitle: "Deploy React App with NGINX"
seoDescription: "Step-by-step guide to deploy a React application with NGINX, from installation to configuration, and enabling your app online"
datePublished: Wed Jul 17 2024 00:55:18 GMT+0000 (Coordinated Universal Time)
cuid: clyp4rvds000508jnh99t59s6
slug: how-to-deploy-a-react-application-with-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721177575417/48a4a3e4-0954-4ddc-8963-0211a2f61010.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1721177694746/f1268d09-bb45-48ef-9c5a-b2e5d5047adb.png
tags: linux, azure, deployment, web-development, nginx, reactjs, devops, howtos

---

How to Deploy a React application with NGINX **(Step-by-Step Guide) 🚀**

*Prerequisites:*

* A basic React project to deploy.
    
* A Linux machine or server.
    
* Domain name (optional).
    

So, you've mastered web development and created a fantastic webapp using react, Now, you're eager to share it with the world. But how do you deploy it on the internet? Fear not; I'm here to guide you through the process.

To get started, you'll need a Linux machine or VM. ([how to create one?](https://hashnode.com/post/clo3b6ngz000509ld6c76dlv0))

### **Step 0 - Connect to your VM (if using cloud)**

connect to your virtual machine using any of the following ways so we can start installing and configuring NGINX server on it.  
A. Connect using ssh-

```bash
ssh ashutosh@192.168.1.7 ↩️
fingerprint(yes) ↩️
yourpassword ↩️

this will start a shell session like-

ashutosh@yourvm:~$
```

B. You can use VNC / RDP, for more info google vnc with your cloud provider term.

You can skip above step if you are setting up NGINX on a local server.

### **Step 1 - Update Your Packages 🔄**

First things first, ensure your system is up-to-date by running this command:

```bash
sudo apt update && sudo apt upgrade
```

💡Pro tip: If you're feeling lazy, you can use `sudo su` to avoid typing `sudo` twice!

### **Step 2 - Install** NGINX **Server 🌐**

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

### **Step 3 - Enable and Configure firewall🔥🧱**

Currently NGINX is running locally, if you try to open the VM's ip in browser it will not show anything, which is obvious as have not enabled `http (80)` and `https(443)` ports from firewall.

```bash
sudo ufw enable
sudo ufw status
sudo ufw allow 'Nginx Full'
sudo ufw status
```

### **Step 4 - Install NodeJs🚂**

Execute following command:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Reload the configuration

```bash
source ~/.bashrc
```

test the installation with `nvm -v` you should see version number.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721176318936/e94bbf21-84a7-4c4e-8527-029fa8968668.png align="center")

finally install NodeJs with `nvm install 21.0.0`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721175744593/70a30140-03e6-49e5-81b6-de4e29afdd40.png align="center")

more on NodeJs installation and NVM here.

### **Step 5 - Verify Your Setup ✅**

After this, your webpage should show up, it's time to see if everything's working. You can do this by typing your server's Public IP address in your web browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718137474636/dfd06f06-efc3-41d8-bf5d-be79ae323709.png?auto=compress,format&format=webp align="left")

### **Step 6 - Creating a simple Website 🌟**

By default, NGINX comes with a basic site enabled. You can customize its content, which is located at `/var/www/html`.

Lets modify default page with our content.

Step 1 - Navigate to default directory

```bash
cd /var/www/html/
ls
sudo rm -r index.html index.nginx-debian.html 
ls
sudo nano index.html
    //if you don't have nano
vim index.html -> i
```

paste this sample html file-

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
    <h1>Hello, World!</h1>
</body>
</html>
```

save and exit

nano -&gt; ctrl+x -&gt; y -&gt; enter.

vim -&gt; :wq -&gt; enter.

Restart the NGINX server

```bash
nginx -t                        //to check the configuratin
sudo systemctl restart nginx    //to restart nginx
```

Then refresh you webpage, it will look something like this-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1718113695292/b8102678-dd8c-49c8-9091-90137f5e7cee.png align="center")

*So this is how you setup a simple static web server with NGINX✨*

## How to host your React web app here?

Now, let’s deploy your React application using NGINX. Follow these steps:

### **Step 7 - Clone Your React Project to NGINX Root Directory 📂**

First, clone your React project into the NGINX root directory.  
You can choose `/var/www/` or any other directory.

```bash
cd /var/www/
sudo git clone https://github.com/yourusername/your-react-project.git
cd your-react-project
```

### **Step 8 - Install Dependencies and Build the Project 📦**

Navigate to your project directory, install dependencies, and build your React application.

```bash
cd /var/www/your-react-project
npm install
npm run build
```

The `build` command will create a `build` directory with your optimized React application.

### **Step 9 - Configure NGINX to Serve Your React Application ⚙️**

Next, configure NGINX to serve your React application. Edit the NGINX configuration file:

```bash
sudo nano /etc/nginx/sites-available/default
```

Replace the contents with the following configuration:

```bash
server {
    ...

    root /var/www/your-react-project/build;
    index index.html index.htm;

    ...
}
```

Save and close the file

### **Step 10 - Restart NGINX Server 🔄**

Finally, restart the NGINX server to apply the changes:

```bash
sudo nginx -t        # To check the configuration
sudo systemctl restart nginx
```

### **Step 11 - Access Your React Application 🥳**

Your React application should now be live. Open your browser and navigate to your server’s public IP or domain name:

```bash
http://yourdomain.com
```

You should see your React app running! 🎉

That's it! You've successfully deployed your React application with NGINX. For adding a domain name, stay tuned for our next blog post.

for any issues you can always reach me out on [**Linkedin**](https://linkedin.com/in/ashutosh7i)

Happy Hacking! ☁️🚀

---