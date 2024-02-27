
# Create docker image and push into AWS ECR

Crate dockerfile and build docker image. push docker image into AMAZON Elastic Container Registry.

### Step 1: Create docker file and run Docker Conatiner.

&nbsp;1. Start docker desktop.

&nbsp;2. Create a docker file.

&nbsp;3. Log into docker 

```
docker log in
```

&nbsp; 4. Buid docker image
```
docker build -t dharmaraj257/hey-nodejs:0.0.1.RELEASE .
```
&nbsp; 5. Run docker container.
```
docker container run -d -p 3000:3000 dharmaraj257/hey-nodejs:0.0.1.RELEASE 
```
### Step 2: Create Amazon Elastic Conatiner Registry

&nbsp; 1. Go to Ecr service and click get started 

&nbsp; 2. Select private and give a Repository name.

&nbsp; 3. Create repository

### Step 3: Log in your aws account using aws cli.
```
aws configure 
AWS Access Key ID [****************2G4Z]:
AWS Secret Access Key [****************Sxmd]:
Default region name [us-east-1]:
Default output format [json]: 
```

### Step 4: Push the docker image into ECR

&nbsp; 1. Select created repository, click view push command and select windows 

&nbsp;  2. Authenticate your docker client to your Registry.
```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin account-id.dkr.ecr.us-east-1.amazonaws.com
``` 
&nbsp; 3.Build your Docker image using the following command. 
```
docker build -t docker-yml .
```
&nbsp; 4.tag your docker image so you can push image the to this repository.
```
docker tag docker-yml:latest account-id.dkr.ecr.us-east-1.amazonaws.com/docker-yml:latest
```
&nbsp; 5.Push this image to your aws repository.
```
docker push account-id.dkr.ecr.us-east-1.amazonaws.com/docker-yml:latest 
```
OutPut:
&nbsp;
![ecr](https://github.com/dharmaraj257/Create-docker-image-and-push-into-AWS-ECR/assets/100831265/119b7f6b-be3c-49c7-a609-d4bd42171a7a)
