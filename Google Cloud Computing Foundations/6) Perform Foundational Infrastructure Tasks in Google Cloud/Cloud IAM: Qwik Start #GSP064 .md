# GSP064

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4893697/labs/403964 \
Video : https://youtu.be/mSVoiD-tN60

## Login with username 1

## Run in cloudshell

```cmd
export USERNAME2=
```

```cmd
touch sample.txt
gsutil mb gs://$DEVSHELL_PROJECT_ID
gsutil cp sample.txt gs://$DEVSHELL_PROJECT_ID
gcloud projects remove-iam-policy-binding $DEVSHELL_PROJECT_ID --member="user:$USERNAME2" --role="roles/viewer"
gcloud projects add-iam-policy-binding $DEVSHELL_PROJECT_ID --member="user:$USERNAME2" --role="roles/storage.objectViewer"
```
