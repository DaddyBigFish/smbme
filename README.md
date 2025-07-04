<img src="https://github.com/user-attachments/assets/ac2ff41c-1fa2-4e83-9a79-812d9ed2b14a" alt="smbme" width="300"/>    


# smbme
### Find writeable folders deep within SMB.

# Description
This was developed to solve the issue when doing simple SMB enumeration of shares. Sometimes folders nested within the share are writable but tools always seem to fail to report it, since it only identifies if the share is writebale or readable. This is confusing, since the share may still be inherently writable if a folder ACL within the share has been set to allow write permissions. The tool 𝘀𝗺𝗯𝗺𝗲 essentially provides the user a way to identify writeable subfolders deep within an SMB share. It essentially connects, verifies the available shares that it can access then it will use smbclient command showacl to read all of the folders permissions. Once a writeable folder is identified it will notify.

# Requirements
```
pip3 install impacket
```
# Install
```
sudo wget https://github.com/DaddyBigFish/smbme/raw/refs/heads/main/smbme -O /usr/local/bin/smbme
sudo chmod +x /usr/local/bin/smbme
```
# Usage
```
smbme xxx.xxx.x.xxx
[+] Identifying shares.... Done.
[+] Identified shares:
✔️ Department Shares
[+] Identifying folders in Department Shares.... Done.
[+] Checking ACL permissions.... Done.
[+] Identified writable folders:
✔️ WRITEABLE!    Department Shares\ZZ_ARCHIVE
✔️ WRITEABLE!    Department Shares\Users\Public
```
