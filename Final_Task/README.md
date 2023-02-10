# GCP - Final Task 

**This repository contains Terraform configuration for setting up infrastructure on Google Cloud Platform (GCP) using Infrastructure as Code (IaC) principles.**

## Requirements
-   Terraform
-   Google Cloud SDK
-   Access to a GCP project with the necessary permissions to create and manage resources.
-   Create a bucket for the terraform state backend

## Flow Chart

![alt](images/GCP-Draw-FinalTask.drawio.png)

## Task

![alt](images/Q.png)

## Getting started

### Local Steps

1. clone this repo :
   ```bash
   git clone https://github.com/95remon/Google-Cloud-Platform-ITI.git
   ```

2. Navigate to Infrastructure-code directory.

3. Change the needed fields as back-end bucket name, Project ID, .... etc.

4. Run terraform commands:
    ```bash
    terraform init
    ```
    ![alt](images/2.png)
    
    ```bash
    terraform apply
    ```
    ![alt](images/3.png)

5. Navigate to Application directory.

6. Build Dockerfile and push image to GCR (Replace "focused-bridge-317713" with your project ID):

    ```bash
    docker build . -t gcr.io/focused-bridge-317713/python-img:v3.0
    ```
    ```bash
    docker push gcr.io/focused-bridge-317713/python-img:v3.0
    ```

### Private VM Steps

1. SSH the VM through browser
2. Update and Install Needed packages
    ```bash
    sudo apt update
    ```
    ```bash
    sudo apt-get install kubectl
    ```
3. Auth login
    ```bash
    gcloud auth login
    ```
4. Connect to cluster (Replace Zone and prject with yours)
    ```bash
    gcloud container clusters get-credentials primary --zone us-central1-a --project focused-bridge-317713
    ```

6. Vim or Upload the YAML files in "YAML-files" path

7. Apply the Deployment in app-deplyment.yaml file
    ```bash
    kubectl apply -f app-deplyment.yaml 
    ``` 

7. Create Loadbalancer service in the LB.yaml file
    ```bash
    kubectl create -f LB.yaml
    ``` 

8. Open the cluster's services and hit the Loadbalancer Endpoint
![alt](images/4.png)
![alt](images/output.png)