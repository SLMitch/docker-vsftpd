## vsftpd


A clean, easy-to-use, tiny yet full-featured installation of vsftpd wrapped in Alpine.

Fork of instantlinux/docker-tools, but without secret, all in environment variable (less secure, but for other workflow)


### Usage

The most-common directives can be specified in environment variables as shown below. If you need further customizations, put them in one or more files under a mount point /etc/vsftpd.d.

A single upload user can be specified via the FTPUSER_xxx variables. 

An example compose file is provided here in docker-compose.yml. This is for the common scenario of sharing from Docker swarm the contents of a network-attached volume as a read-only anonymous-ftp service.

Status: DO NOT USE. I've had constant segfault crashes with vsftpd version 3.0.3 under Alpine and Ubuntu. I've switched to proftpd (see that image).

### Variables

Variable | Default | Description |
-------- | ------- | ----------- |
ANONYMOUS_ENABLE | YES | Anonymous login
ANON_MKDIR_WRITE_ENABLE | NO | Anonymous mkdir
ANON_UPLOAD_ENABLE | NO | Anonymous upload
FTPUSER_PASSWORD | ftppassword | pw of upload user
FTPUSER_NAME | ftpuser | upload username
FTPUSER_UID | 1001 | upload file ownership UID
LOCAL_UMASK | 022 | upload umask
LOG_FTP_PROTOCOL | NO | more-verbose logging
PASV_ADDRESS |  | required--address of docker engine
PASV_MAX_PORT | 30100 | range of client ports (rebuild image if changed)
PASV_MIN_PORT | 30091 | 
TZ | UTC | local timezone
USE_LOCALTIME | YES | local time for directory listing
VSFTPD_LOG_FILE | /dev/stdout | logfile destination
WRITE_ENABLE | YES | allow put/rm
