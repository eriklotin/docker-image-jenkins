# Docker image: eriklotin/jenkins

Jenkins image with docker support.

# Usage example

Pull image from Docker Hub
```bash
docker pull eriklotin/jenkins
```
or build from Dockerfile
```bash
docker build . -t eriklotin/jenkins
```

Run container and create docker group for jenkins user:

```bash
docker run --name jenkins -d \
                -v /var/run/docker.sock:/var/run/docker.sock \
                -v $(which docker):/usr/bin/docker \
                -p 8080:8080 eriklotin/jenkins   
                
docker exec jenkins sudo groupadd docker -g $(ls -aln /var/run/docker.sock  | awk '{print $4}')

docker exec jenkins sudo usermod -aG docker jenkins
```
