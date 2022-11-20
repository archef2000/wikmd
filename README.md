# WIKMD docker container
Multiarch wikmd docker container from [Linbreux](https://github.com/Linbreux/wikmd).

# Docker Compose
```
version: "2.1"
services:
  wikmd:
    image: archef200/wikmd:latest
    container_name: wikmd
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Paris
      - HOMEPAGE=homepage.md #optional
      - HOMEPAGE_TITLE=homepage.md #optional
      - WIKMD_LOGGING=1 #optional
    volumes:
      - /path/to/wiki:/wiki
    ports:
      - 5000:5000
    restart: unless-stopped
```

# Docker run
```
docker run -d \
  --name wikmd \
  -e TZ=Europe/Paris \
  -e PUID=1000 \
  -e PGID=1000 \
  -e HOMEPAGE=homepage.md `#optional` \
  -e HOMEPAGE_TITLE=homepage.md `#optional` \
  -e WIKMD_LOGGING=1 `#optional` \
  -p 5000:5000 \
  -v /path/to/wiki:/wiki \
  --restart unless-stopped \
  archef200/wikmd:latest
```

# Variables,
## Environment Variables
| Variable | Required | Function | Example |
|----------|----------|----------|----------|
|`PUID`|yes|for UserID|`PUID=1000`|
|`PGID`|yes|for GroupID|`PGID=1000`|
|`TZ`|yes|Specify a timezone to use EG Europe/Paris|`TZ=Europe/Paris`|
|`HOMEPAGE`|no|Specify the file to use as a homepage|`HOMEPAGE=homepage.md`|
|`HOMEPAGE_TITLE`|no|Specify the homepage's title|`HOMEPAGE_TITLE=title`|
|`WIKMD_LOGGING`|no|Enable/disable file logging|`WIKMD_LOGGING=1`|

## Volumes
| Volume | Required | Function | Example |
|----------|----------|----------|----------|
| `/wiki` | Yes | Markdown files | `/path/to/wiki:/wiki`|

## Ports
| Port | Proto | Required | Function | Example |
|----------|----------|----------|----------|----------|
| `5000` | TCP | Yes | wikmd server TCP listening port | `5000:5000/tcp`|
