DirectDownload provides an easy way to downloads files from the device running aria2 directly to your device.

This guide will discuss two ways to do this:
* [with Python](#with-python)
* [with Apache](#with-apache)

# Server-side setup
In order to make DirectDownload work we need to setup a service that provides direct access to the files that are being downloaded by aria2. Below is explained one of the many ways to do it. For this method you need Python installed. 

## With Python

### Python installation
- **Linux**: Python on Linux can be installed with apt: `sudo apt-get install python` or `sudo apt-get install python3`. If your system doesn't have apt you can use any other package manager, they should all provide python. 
- **Windows**: Python for Windows can be downloaded [here](https://www.python.org/downloads/windows/). Any version should do it. 
- **Mac OS X**: Python for Mac OS X can be downloaded [here](https://www.python.org/downloads/mac-osx/). Any version should do it. 

### Running the script
Running the script is as simple as typing a single command in the aria2 download directory (specified by the `--dir` option): for Python < 3 type `python -m SimpleHTTPServer [port number]` and for Python > 3 type `python -m http.server [port number]`. 

>**Note for Linux**: you may need to run the command as root with sudo.

>**Note for Windows**: a Windows Firewall alert may appear on the screen asking for access to the external network. In order to make the script work you need to grant the access.

>**Note**: if you're going to connect to the server from an external network, you need to open the desired port on you router.

### Advanced server-side setup
DirectDownload supports both authentication with [Authorization](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication) header and download resuming with the [Range](https://developer.mozilla.org/en-US/docs/Web/HTTP/Range_requests) header. 

### Python script
I have created a Python script to do all the job for you. This script supports all the features provided by DirectDownload. You can find the script [here](https://gist.github.com/devgianlu/018b299f8817bf92350bf7bf70214e4d). To download it use wget or your browser. 

>**Note**: Python > 3.7 is required

>**Example**: To download with wget just type `wget https://gist.githubusercontent.com/devgianlu/018b299f8817bf92350bf7bf70214e4d/raw/4ebe6b4a6899fd297683810d1ea0ade4d2bfb92e/serve_http.py`

Once you downloaded the file execute it with the python like so: `python ./serve_http.py`

>**Note for Linux**: you may need to run the command as root with sudo.

>**Note for Windows**: a Windows Firewall alert may appear on the screen asking for access to the external network. In order to make the script work you need to grant the access.

>**Note**: if you're going to connect to the server from an external network, you need to open the desired port on you router.

### Authentication
You can also set an username and password to access the files, that can be done by editing line 247-248 like so:
```
USERNAME = "username123"
PASSWORD = "password456"
```

## With Apache

### Installing Apache
- **Linux**: do `sudo apt-get install apache2` from the terminal
- **Windows**: [download from here](https://httpd.apache.org/docs/2.4/platform/windows.html)

## Configuration
The setup is pretty simple:
- Create a configuration file inside the `sites-enabled` folder (`/etc/apache2/sites-enabled` on Linux) named something you can relate to `aria2`, the filename should end with `.conf`.
- Inside this file copy the following text, editing it as mentioned below:
```
<VirtualHost *:[PORT]>
        DocumentRoot [DIR]
        <Directory [DIR]>
                Options +Indexes
                Order allow,deny
                Allow from all
                Require all granted
                DirectoryIndex disabled
        </Directory>
</VirtualHost>
```
> Replace `[PORT]` with the desired port number (avoid small numbers, but less than 65536) and `[DIR]` with the full path to your downloads folder.
- Restart Apache: ` sudo systemctl restart apache2` or the equivalent for your system.

> **Note**: if you encounter permission problems (403) check your folder permissions, you main need to `chown -R www-data:www-data [DIR]` or `chmod -R o+r [DIR]`.


# Aria2App setup
Once your script is running, you need to gather the IP address of the machine. When you have it you can type in the address field of DirectDownload in Aria2App the full address pointing to the directory listing.

>**Example**: If the address is 192.168.1.8 and the port is 801, then the full address is http://192.168.1.8:801/.

>**Note**: HTTPS is also supported.