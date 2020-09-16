DirectDownload allows to download files from a Samba share.

# Server-side setup

Install an SMB client and configure it to have access to the downloads folder of aria2, it doesn't need to be the root directory (check some tutorials online).

# Client-side setup

Gather the machine IP (or hostname), the share name and the relative path to the downloads directory, select the `SAMBA` mode and insert the data. Anonymous login is also supported.