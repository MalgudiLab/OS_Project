# Apache Web Server Installation and Configuration Guide

Apache Web Server is a widely used software that enables you to host websites on the internet. It acts like a bridge between your web browser and the files that make up a website. When you enter a website address, Apache retrieves the necessary files and delivers them to your browser, allowing you to view the site. Being open-source and highly customizable, Apache can handle everything from small personal blogs to large commercial sites, making it a versatile choice for web hosting.

---

## Prerequisites
- A Linux server (Ubuntu, Debian, CentOS, RHEL).
- Basic command-line knowledge.
- Administrative access to the system.

---

## Installing Apache

### On Ubuntu/Debian:
```bash
sudo apt update
sudo apt install apache2
```

### On CentOS/RHEL:
```bash
sudo yum install httpd
```

---

## Starting and Enabling Apache

### On Ubuntu/Debian:
```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

### On CentOS/RHEL:
```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

To check if the service is running:
```bash
sudo systemctl status apache2
```

### Expected Output:
```
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2022-04-26 15:33:21 UTC; 43s ago
   Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 5089 (apache2)
   Tasks: 55 (limit: 1119)
   Memory: 4.8M
   CPU: 33ms
   CGroup: /system.slice/apache2.service
           ├─5089 /usr/sbin/apache2 -k start
           ├─5091 /usr/sbin/apache2 -k start
           └─5092 /usr/sbin/apache2 -k start
```

---

## Configuring Apache

The default configuration file is located at:
- **Ubuntu/Debian**: `/etc/apache2/apache2.conf`
- **CentOS/RHEL**: `/etc/httpd/conf/httpd.conf`

Edit the configuration file using a text editor, like `nano` or `vim`:
```bash
sudo nano /etc/apache2/apache2.conf  # For Ubuntu/Debian
sudo nano /etc/httpd/conf/httpd.conf  # For CentOS/RHEL
```

To change the default document root (where your web files will be stored), locate the `DocumentRoot` directive and modify it:
```bash
DocumentRoot /var/www/html
```

Ensure the directory exists; create it if necessary:
```bash
sudo mkdir -p /var/www/html
```

---

## Creating a Simple Web Page

### Step 1: Create a Directory for Your Website
```bash
sudo mkdir /var/www/mtl/
```

### Step 2: Create an HTML File
Go into the newly created directory:
```bash
cd /var/www/mtl/
nano index.html
```

### Step 3: Add HTML Content
Paste the following code into the `index.html` file:
```html
<html>
<head>
    <title>Hello MaalGudi</title>
</head>
<body>
    <h1>Heyy Maalgudians !!</h1>
    <p>I'm running this website on an Apache Server!</p>
</body>
</html>
```

---

## Setting Up a VirtualHost Configuration File

### Step 1: Create and Edit the VirtualHost File
Go to the configuration files directory:
```bash
cd /etc/apache2/sites-available/
sudo cp 000-default.conf gci.conf
sudo nano gci.conf
```

### Step 2: Update Configuration
- **ServerAdmin**: Add your email address for users to contact in case of errors.
  ```bash
  ServerAdmin yourname@example.com
  ```

- **DocumentRoot**: Update the directive to point to your website directory.
  ```bash
  DocumentRoot /var/www/mtl/
  ```

- **ServerName**: Add this directive to define your domain/subdomain.
  ```bash
  ServerName mtl.example.com
  ```

---

## Activating the VirtualHost File

Enable the VirtualHost configuration:
```bash
sudo a2ensite gci.conf
```

Restart Apache to apply changes:
```bash
sudo service apache2 reload
```

---

## Testing the Installation

Open a browser and navigate to your hostname:
```
http://mtl.example.com
```

You should see your website live!

---

## Conclusion

You have successfully installed and configured the Apache Web Server. With a custom VirtualHost and a simple webpage hosted, your server is ready for further customizations and hosting.