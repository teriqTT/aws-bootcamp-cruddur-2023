# Week 1 — App Containerization

## Run the Dockerfile CMD as an external script. Of note Health check is also implemented in my dockerfile.
FROM golang:1.15.3 as builder
WORKDIR /app/
COPY . .
RUN go build -o app /app/main.go

FROM alpine:latest
WORKDIR /app/
COPY --from=builder /app/ /app/


HEALTHCHECK CMD curl --fail http://localhost:3000 || exit 1  

CMD ./app

### Code for the App Used in the above example.
package main
import (
	"fmt"
)

func main() {
	fmt.Println("Hello Docker this is a test for Cloud Project Bootcamp!")
	
}


## Evidence to demonstrate that Docker was installed on my local computer.
![image](https://user-images.githubusercontent.com/101008098/221363593-adeed9b9-83c9-4c6d-8f3a-798920f4f4d6.png)



## Evidence to show that I tagged an image and pushed it to Dockerhub.
https://hub.docker.com/layers/celenem/testimage/1.0.0/images/sha256-8ba91b6654ab7e22a29a2ce4e9c4bf0178261a805302dbdb9ac5ff9a7fbfa196?context=repo
----------------------------------------------------------------------------------------------------------------------------------------------------
![image](https://user-images.githubusercontent.com/101008098/221363532-c1c6d6b6-1811-4536-8d22-df25a0f88a2d.png)


## Evidence to show that I installed docker in an EC2 instance and pulled publically available images from dockerhub to the container. I have also demonstrated that I pulled my own public dockerhub image.
![image](https://user-images.githubusercontent.com/101008098/221363119-9ef8617b-e659-4029-912e-672f418f79f7.png)
------------------------------------------------------------------------------------------------------------------------------------------------------
![image](https://user-images.githubusercontent.com/101008098/221363435-70b2f604-8c6d-4be3-b1a3-a19940e4e5ad.png)

