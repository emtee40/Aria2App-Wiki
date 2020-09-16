DirectDownload allows to download files from a SFTP (SSH) server.

# Server-side setup

Install an SSH server (`openssh` probably) and configure it (there are plenty tutorials online).

# Client-side setup

Gather the machine IP, the SSH port you're using (22 by default), the username and password, select `SFTP` mode and insert the data. You **must** also press the verify button to check the server fingerprint which will be the only one accepted for future connections.

> Authenticating with SSH keys is not supported.