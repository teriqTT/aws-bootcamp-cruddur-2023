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



## Evidence to show that I tagged an image and pushed it to Dockerhub.



## Evidence to show that I installed docker in an EC2 instance and pulled publically available images from dockerhub to the container. I have also demonstrated that I pulled my own public dockerhub image.
