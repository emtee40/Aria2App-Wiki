DirectDownload provides an easy way to downloads files from the device running aria2 directly to your device.

## Server-side setup
In order to make DirectDownload work we need to setup a service that provides direct access to the files that are being downloaded by aria2. Below is explained one of the many ways to do it. For this method you need Python installed. 

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

## Aria2App setup
Once your script is running, you need to gather the IP address of the machine. When you have it you can type in the address field of DirectDownload in Aria2App the full address pointing to the directory listing. Remember that any path added to the end of the address will be ignored.

>**Example**: If the address is 192.168.1.8 and the port is 801, then the full address is http://192.168.1.8:801/.

>**Note**: HTTPS is also supported.

You can also specify to use basic authentication, which is not provided by this script.