## 👋 Welcome to lidarr 🚀  

Lidarr is a music collection manager for Usenet and BitTorrent users.  
It can monitor multiple RSS feeds for new tracks from your favorite artists and will grab, sort and rename them.  
It can also be configured to automatically upgrade the quality of files already downloaded when a better quality format becomes available  
  
  
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
-v /mnt/music:/music:z \
-v /mnt/downloads:/downloads:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/config:/config:z \
-p 0.0.0.0:8686:8686 \
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
      - /mnt/music:/music:z
      - /mnt/downloads:/downloads:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-lidarr/rootfs/config:/config:z
    ports:
      - 0.0.0.0:8686:8686
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
