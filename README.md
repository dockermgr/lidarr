## 👋 Welcome to lidarr 🚀  

lidarr README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update lidarr
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/lidarr/rootfs"
git clone "https://github.com/dockermgr/lidarr" "$HOME/.local/share/CasjaysDev/dockermgr/lidarr"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/lidarr/rootfs/." "$HOME/.local/share/srv/docker/lidarr/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-lidarr \
--hostname lidarr \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/config:/config:z \
-p 80:80 \
casjaysdevdocker/lidarr:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/lidarr
    container_name: casjaysdevdocker-lidarr
    environment:
      - TZ=America/New_York
      - HOSTNAME=lidarr
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/config:/config:z
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/lidarr
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/lidarr" "$HOME/Projects/github/casjaysdevdocker/lidarr"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/lidarr"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
