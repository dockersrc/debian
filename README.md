## 👋 Welcome to debian 🚀  

debian README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update os debian
```
  
## Install and run container
  
```shell
mkdir -p "/var/lib/srv/root/docker/casjaysdev/debian/latest"
git clone "https://github.com/dockermgr/debian" "$HOME/.local/share/CasjaysDev/dockermgr/debian"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/debian/rootfs/." "/var/lib/srv/root/docker/casjaysdev/debian/latest/"
docker run -d \
--restart always \
--privileged \
--name casjaysdev-debian-latest \
--hostname debian \
-e TZ=${TIMEZONE:-America/New_York} \
-v "/var/lib/srv/root/docker/casjaysdev/debian/latest/data:/data:z" \
-v "/var/lib/srv/root/docker/casjaysdev/debian/latest/config:/config:z" \
casjaysdev/debian:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdev/debian
    container_name: casjaysdev-debian-latest
    environment:
      - TZ=America/New_York
      - HOSTNAME=debian
    volumes:
      - "/var/lib/srv/root/docker/casjaysdev/debian/latest/data:/data:z"
      - "/var/lib/srv/root/docker/casjaysdev/debian/latest/config:/config:z"
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src os debian
```
  
## Build container  
  
```shell
git clone "https://github.com/dockersrc/debian" "$HOME/Projects/github/dockersrc/debian"
cd "$HOME/Projects/github/dockersrc/debian" && buildx all 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdev: [Github](https://github.com/dockersrc) [Docker](https://hub.docker.com/u/casjaysdev) ⛵  
