# GSP154

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892605/labs/377394 \
Video : https://youtu.be/61XMPrGqqyw

## Run in cloudshell

```cmd
gcloud services enable videointelligence.googleapis.com
gcloud iam service-accounts create quickstart
gcloud iam service-accounts keys create key.json --iam-account quickstart@$DEVSHELL_PROJECT_ID.iam.gserviceaccount.com
gcloud auth activate-service-account --key-file key.json
gcloud auth print-access-token
cat > request.json <<EOF
{
   "inputUri":"gs://spls/gsp154/video/train.mp4",
   "features": [
       "LABEL_DETECTION"
   ]
}
EOF
export RESPONSE=$(curl -s -H 'Content-Type: application/json' -H 'Authorization: Bearer '$(gcloud auth print-access-token)'' 'https://videointelligence.googleapis.com/v1/videos:annotate' -d @request.json | jq -r '.name')
curl -s -H 'Content-Type: application/json' \
-H 'Authorization: Bearer '$(gcloud auth print-access-token)'' \
"https://videointelligence.googleapis.com/v1/$RESPONSE"
```
