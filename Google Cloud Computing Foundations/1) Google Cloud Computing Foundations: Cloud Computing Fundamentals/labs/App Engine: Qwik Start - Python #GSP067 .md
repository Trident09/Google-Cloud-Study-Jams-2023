# GSP067

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4891692/labs/376202 \
Video : https://youtu.be/s2U8pXpRXpI

## Run in Cloudshell

```cmd
gcloud services enable appengine.googleapis.com
git clone https://github.com/GoogleCloudPlatform/python-docs-samples.git
cd python-docs-samples/appengine/standard_python3/hello_world
sed -i 's/Hello World!/Hello, Cruel World!/g' main.py
gcloud app deploy
```

### Select the Region from task 5 step 2 (As you select the region check the progress)
