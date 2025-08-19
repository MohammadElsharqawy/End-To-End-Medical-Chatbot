# End-To-End-Medical-Chatbot

# How to run?
### STEPS

Clone the repository

```bash
https://github.com/MohammadElsharqawy/End-To-End-Medical-Chatbot
```
### STEP 01- Create virtual environment afetr opening the repository

```bash
conda create -n medical python=3.10 -y
```

```bash
conda activate medical
 ```


 ### STEP 02- install the requirements
 ```bash
 pip install -r requirements.txt
 ```

 ### Create a .env file in the root directory and add your Pinecone & openai credentials as follows:
bash
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"



### run the following command to store embeddings to pinecone
bash
python store_index.py



### Finally run the following command
bash
python app.py


### Now, open up local host at port 8080



### Technology Stack

- Python
- LangChain
- Flask
- GPT 
- PineCone


## AWS-CICD-Deployment-with-Github-Actions

### 1. Login to AWS console.

### 2. Create IAM user for deployment with specific access and create access and secret keys


```bash
Policy:
1. AmazonEC2ContainerRegistryFullAccess

2. AmazonEC2FullAccess
```

### glimpse of the workflow


    1. Build docker image of the source code

    2. Push your docker image to ECR

    3. Launch Your EC2 

    4. Pull Your image from ECR in EC2

    5. Lauch your docker image in EC2



### 3. Create ECR repo to store/save docker image

```bash
- Save the URI: 315865595366.dkr.ecr.us-east-1.amazonaws.com/medicalbot
```

### 4. Create EC2 machine (Ubuntu)

### 5. Open EC2 and Install docker in EC2 Machine :

```bash

# optinal

sudo apt-get update -y

sudo apt-get upgrade

# required

curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

sudo usermod -aG docker ubuntu

newgrp docker
```

### open the required port -(inpounf rules) ex. 8080- in youe EC2 instance'

### 6. Configure EC2 as self-hosted runner in github:

```bash
setting>actions>runner>new self hosted runner> choose os> then run command one by one
```

## 7. Setup github secrets:
  -  AWS_ACCESS_KEY_ID
  -  AWS_SECRET_ACCESS_KEY
  -  AWS_DEFAULT_REGION
  -  ECR_REPO
  -  PINECONE_API_KEY
  -  OPENAI_API_KEY