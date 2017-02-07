# vsftpd-alpine
Docker image of vsftpd server based on Alpine 3.4 

##Exemple usage
```
docker run \
  --name vsftpd \
  -d \
  -e FTP_USER=www \
  -e FTP_PASS=my-password \
  -e PASV_ADDRESS=5.6.7.8 \
  -e PASV_MIN=21100 \
  -e PASV_MAX=21110 \
  -p 21:21 \
  -p 21100-21110:21100-21110 \
  avenus/vsftpd-alpine
```

##Exemple usage in compose file
```
version: '3'
services:
  ftp:
   image: avenus/vsftpd-alpine
   ports:
     - "35000:21"
     - "21100-21110:21100-21110"
   volumes:
    - some-volume:/home/user/
    - /home/ftp/logs/:/var/log/
   environment:
    - FTP_USER=user
    - FTP_PASS=my-password
    - PASV_ADDRESS=5.6.7.8
    - PASV_MIN=21100
    - PASV_MAX=21110
```
