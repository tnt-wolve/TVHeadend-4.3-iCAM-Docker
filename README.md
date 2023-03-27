# TVHeadend-4.3-iCAM-Docker

Configures like the [linuxserver container](https://hub.docker.com/r/linuxserver/tvheadend)

### docker-cli
```
docker run -d \
  --name=tvheadend \
  -e PUID=1000 \
  -e PGID=1000 \
  -e TZ=Etc/UTC \
  -e RUN_OPTS= `#optional` \
  -p 9981:9981 \
  -p 9982:9982 \
  -v /path/to/data:/config \
  -v /path/to/recordings:/recordings \
  --device /dev/dri:/dev/dri `#optional` \
  --device /dev/dvb:/dev/dvb `#optional` \
  --restart unless-stopped \
  chris230291/tvheadend:latest
```

### docker-compose
```
---
version: "2.1"
services:
  tvheadend:
    image: chris230291/tvheadend:latest
    container_name: tvheadend
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
      - RUN_OPTS= #optional
    volumes:
      - /path/to/data:/config
      - /path/to/recordings:/recordings
    ports:
      - 9981:9981
      - 9982:9982
    devices:
      - /dev/dri:/dev/dri #optional
      - /dev/dvb:/dev/dvb #optional
    restart: unless-stopped
```
