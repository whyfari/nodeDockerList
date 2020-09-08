# remove image if it already exists
```
docker images |  grep appimage
docker image rm appimage

docker images |  grep demo-app 
docker image rm whyfari/demo-app
```

# build docker image
- build docker image using the 'Dockerfile', name image 'appimage'
```
docker build . -t appimage
```

# OR Get image from docker hub 

```
docker pull whyfari/demo-app
```

# run container using image
- run a container (name it app01) using the image (pulled from docker or build manually running)
- expose container port 8080 to local 8080
- on wsl was can't hit private ip (looked up via docker inpsect) outside in windows using the the browser even though I can curl it inside wsl

```
# pull or used pulled from docker hub
docker run --rm -dt --name app01 -p 8080:8080 whyfari/demo-app

# use built image 
docker run --rm -dt --name app02 -p 8081:8080 appimage

```

# visit website
```
curl localhost:8080
```
- visit it on localhost

http://localhost:8080/
http://localhost:8081/

- IP of wsl (ip, ifconfig | grep eth0 -A 1)
```
<ip>:8080
<ip>:8081
172.21.215.133:8080
172.21.215.133:8081
```

# stop container 
- will also remove the container since we started with --rm
```
docker stop app01
docker stop app02
```

