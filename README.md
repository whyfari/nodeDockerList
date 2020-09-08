## build docker image
```
docker build . -t appimage
```

## run container using image
- run a container using the image, expose port to local
- on wsl was having issues w/o exposing to localhost because I ciouldn't access the private ip (looked up via docker inpsect) outside in the browser even though I can curl it inside wsl

```
docker run -dt --name app01 appimagedocker run --rm -dt --name app01 -p 8080:8080 appimage
```

## visit website
```
curl localhost:8080
```

- visit it on localhost

http://localhost:8080/

- IP of wsl (ip, ifconfig | grep eth0 -A 1)l
<ip>:8080
172.21.215.133:8080

## stop container 
```
docker stop app01
```

