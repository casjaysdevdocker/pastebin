## 👋 Welcome to pastebin 🚀  

pastebin README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update pastebin
```
  
## Install and run container
  
```shell
dockerHome="/srv/$USER/docker/casjaysdevdocker/pastebin/pastebin/latest/rootfs"
mkdir -p "/srv/$USER/docker/pastebin/rootfs"
git clone "https://github.com/dockermgr/pastebin" "$HOME/.local/share/CasjaysDev/dockermgr/pastebin"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/pastebin/rootfs/." "$dockerHome/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-pastebin-latest \
--hostname pastebin \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$dockerHome/data:/data:z" \
-v "$dockerHome/config:/config:z" \
-p 80:80 \
casjaysdevdocker/pastebin:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/pastebin
    container_name: casjaysdevdocker-pastebin
    environment:
      - TZ=America/New_York
      - HOSTNAME=pastebin
    volumes:
      - "/srv/$USER/docker/casjaysdevdocker/pastebin/pastebin/latest/rootfs/data:/data:z"
      - "/srv/$USER/docker/casjaysdevdocker/pastebin/pastebin/latest/rootfs/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/pastebin
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/pastebin" "$HOME/Projects/github/casjaysdevdocker/pastebin"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/pastebin"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
