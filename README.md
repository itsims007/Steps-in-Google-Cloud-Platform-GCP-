# Steps-in-Google-Cloud-Platform-GCP-

<h2>Environments and Technologies Used</h2>

- Free Google Cloud Trial (GCP)
  
<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2> Deployment and Configuration Steps</h2>

Step One - Create Free Google Cloud Platform Trial account on (https://cloud.google.com/free/)

Step Two - - Access the Google Cloud Console ([console.cloud.google.com](http://console.cloud.google.com/)) **and log in with your newly created account**
- Open the Cloud Shell
- Download the mission1.zip file in the Google Cloud shell using the wget command
- Upload the key.csv file to the Cloud Shell using the browser

Step Three - Verify if the mission1.zip and key.csv files are in the folder in the Cloud Shell using the command below
- Execute the file preparation commands:
    - unzip mission1.zip
    - mv key.csv mission1/en
    - cd mission1/en
    - chmod +x *.sh
- Execute the commands below to prepare the AWS and GCP environment
    - mkdir -p ~/.aws/
    - touch ~/.aws/credentials_multiclouddeploy
    - ./aws_set_credentials.sh key.csv
    - GOOGLE_CLOUD_PROJECT_ID=$(gcloud config get-value project)
    - gcloud config set project $GOOGLE_CLOUD_PROJECT_ID
    -Click on Authorize
- Execute the command below to set the project in the Google Cloud Shell
    - ./gcp_set_project.sh
- Execute the commands to enable the Kubernetes, Container Registry, and Cloud SQL APIs
    - gcloud services enable containerregistry.googleapis.com
    - gcloud services enable container.googleapis.com
    - gcloud services enable sqladmin.googleapis.com
    - gcloud services enable cloudresourcemanager.googleapis.com
    - gcloud services enable serviceusage.googleapis.com
    - gcloud services enable compute.googleapis.com
    - gcloud services enable servicenetworking.googleapis.com --project=$GOOGLE_CLOUD_PROJECT_ID
