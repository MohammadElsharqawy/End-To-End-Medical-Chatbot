
## 📌 Project Description

### End-to-End Medical Chatbot with LangChain, Pinecone, and AWS Deployment

##### This project implements a Retrieval-Augmented Generation (RAG) pipeline for a medical chatbot, integrating LangChain, Sentence-BERT embeddings, Pinecone serverless vector DB on AWS, and GPT-4o for natural language generation. The chatbot is served via a Flask web application, containerised with Docker, and deployed on AWS EC2 using GitHub Actions CI/CD.

### 🔑 Key Features

   - LangChain RAG Pipeline: Combines Sentence-BERT Hugging Face embeddings with Pinecone vector store and GPT-4o for accurate, context-aware responses.

   - Flask Web Application: Simple frontend for querying the chatbot and retrieving answers.

   - Pinecone Serverless on AWS: Stores and retrieves embeddings for scalable, low-latency search.

   - Dockerised Deployment: Application packaged as a Docker image.

   - CI/CD with GitHub Actions: Automated workflow to build, push Docker images to Amazon ECR, and deploy to EC2 via self-hosted runners.

   - Secure Configuration: API keys and AWS credentials stored in GitHub Secrets, with environment variables managed via .env.


 ###  Deployment Workflow

1- Build and containerise the Flask + LangChain application with Docker.

2- Push image to Amazon Elastic Container Registry (ECR).

3- Launch and configure EC2 instance with Docker.

4- Pull latest image from ECR and run containerised chatbot.

5- CI/CD pipeline ensures automatic redeployment on each push to main
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
- Save the URI: 597088048829.dkr.ecr.eu-north-1.amazonaws.com/medicalbot
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