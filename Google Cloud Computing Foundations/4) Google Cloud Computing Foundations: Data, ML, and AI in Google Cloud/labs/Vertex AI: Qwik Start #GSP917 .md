# GSP917

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892605/labs/377385 \
Video : https://youtu.be/Gi5WbrulMfM

## Run in cloudshell

```cmd
gcloud services enable \
compute.googleapis.com \
iam.googleapis.com \
iamcredentials.googleapis.com \
monitoring.googleapis.com \
logging.googleapis.com \
notebooks.googleapis.com \
aiplatform.googleapis.com \
bigquery.googleapis.com \
artifactregistry.googleapis.com \
cloudbuild.googleapis.com \
container.googleapis.com
SERVICE_ACCOUNT_ID=vertex-custom-training-sa
gcloud iam service-accounts create $SERVICE_ACCOUNT_ID  \
--description="A custom service account for Vertex custom training with Tensorboard" \
--display-name="Vertex AI Custom Training"
PROJECT_ID=$(gcloud config get-value core/project)
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
--role="roles/storage.admin"
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
--role="roles/bigquery.admin"
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
--role="roles/aiplatform.user"
```

## Now do task 3 manually

### Vertex AI > Workbench > Enable Notebooks API > User Managed Notebooks > Create New 

### New Instance > Environment = 
```TensorFlow Enterprise 2.x (with LTS)```

### Name = Any Name 
### Fill region Given in lab and any zone within the region 
### Advanced Options > Machine = E2 - Standard - 2 > Create > Open JupiterLab
### Click Terminal 
```cmd
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```
