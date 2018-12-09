## Connectivity conditions
Aria2App is able to choose which connection parameters to use based on the actual connectivity condition. Every profile can be set up with addresses for each connectivity condition or one to use always. If the profile has more than one condition, one must be specified as default in case none of the other conditions matches the situation. 

There are 5 different conditions:
- Always
- Wifi
- Mobile
- Bluetooth
- Ethernet

#### Always
Uses always the same address whether the user is connected to a Wifi, a mobile network or what ever else.
>**Note**: one profile can't contains both "always" and one of the other conditions, as they would be overridden by this one.

#### Wifi
Used when the user is connected to a wifi of which the SSID must be specified. 

#### Mobile
Used when the user is connected to a mobile network. 

#### Bluetooth
Used when the user is connected to a bluetooth hotspot. 

#### Ethernet
Used when the user is connected to an ethernet connection.

## Connection
Setting up the connection address is quite simple. Only the address and the port on which aria2 is listening are strictly necessary. The address field should be filled with only the address without the scheme and the port, the port field tasks only the port number and the endpoint can be left unchanged.
>**Example**: If the complete address is ws://example.com:6800/jsonrpc, then the address is example.com and the port is 6800.

## Encryption
Connection encryption via SSL/TLS is also supported. To enable it just tick the checkbox. If you are using a self-signed certificate, enter a full path to the client certificate or install the certificate system-wide. The file must be the same supplied to aria2 with the `--rpc-certificate` option.

## Authentication
Authentication can either be via token, via username and password or disabled. However be aware of the fact that authentication via username and password is deprecated (See [aria2 manual](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-rpc-passwd)).

## DirectDownload
To understand how DirectDownload work and how to set it up go [here](/docs/Aria2App/setup-directdownload/).