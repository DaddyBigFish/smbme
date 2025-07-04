<img src="https://github.com/user-attachments/assets/ac2ff41c-1fa2-4e83-9a79-812d9ed2b14a" alt="smbme" width="300"/>    


# smbme
### Find writeable folders deep within SMB.

# Description
This was developed to solve the issue of understanding ACLs during SMB enumeration. Sometimes folders nested within a share are writable but all the tools I've used always seem to fail to report it since they are only identifying if the share itself is writebale or readable. This is confusing, because the share may still be inherently writable if a folder's ACL within the share has been set to allow write permissions. The tool 𝘀𝗺𝗯𝗺𝗲 provides the solution for this. It gives the user a way to identify writeable subfolders deep within an SMB share. It essentially connects, verifies accessible shares, it enumerates deep into the folder structure, then finally uses smbclient's showacl to read all of the folder's permissions to identify **SID: S-1-1-0 (Everyone)** and **Permissions: 0x1f01ff (Write)**.

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
