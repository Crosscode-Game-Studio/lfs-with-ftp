## Git with FTP for LFS

Install curlftpfs, git and git-lfs with : `sudo apt install curlftpfs git git-lfs -y`  

Then install [lfs-folderstore](https://github.com/sinbad/lfs-folderstore/releases) in `/home/user/bin` (do not forget to chmod +x).  

Reboot your computer.  

Create a folder for your FTP mount : `mkdir /home/user/ftp`  

Mount ftp in the folder : `curlftpfs -o user='user:pass' ftp://yourftpdomain.com/ /home/user/ftp -v`  

In your project you then have to do these commands :  

```sh
git init

# Configure LFS
git config --add lfs.customtransfer.lfs-folder.path lfs-folderstore
git config --add lfs.customtransfer.lfs-folder.args "/home/user/ftp"
git config --add lfs.standalonetransferagent lfs-folder
```

You can then test your setup by pushing LFS files.
