
# Overview

This project modifies mtwo/front-end to work on Amazon Xray.

## Customize and Rebuild [mtwo/microservices-demo](https://github.com/mtwo/front-end)

### Rebuild Node Modules

    nvm install 4.8.1
    npm install  #this may take a while and may break (see troubleshooting)

### Build Image

    docker build -t repo/mtwo-front-end:v1 .
    docker push repo/mtwo-front-end:v1

### Sock Shop 

[See Sock Shop Docs for more information on Sock Shop](https://microservices-demo.github.io/deployment/kubernetes.html)

#### Update Deployment for Sock Shop

After you've updated your image, you'll need to update your Kubernetes deployment configuration and redeploy. 

    nano complete-demo.yaml

change image path

    spec:
      replicas: 1
      template:
        metadata:
          labels:
            name: front-end
        spec:
          containers:
          - name: front-end
            image: repo/mtwo-front-end:v1

 
#### Redeploy Sock Shop

  kubectl apply -f complete-demo.yaml




###  Troubleshooting
if you get errors with npm install , do this:

    npm cache clean –force
    rm ~/.npm ~/.npm-old
    mkdir -p ~/.npm

You may also want to reset your git branch

    git reset --hard




