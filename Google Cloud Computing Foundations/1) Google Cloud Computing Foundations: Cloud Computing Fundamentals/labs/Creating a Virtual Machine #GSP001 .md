# GSP001

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4891692/labs/376198 \
Video : https://youtu.be/y__7BQQVXwY

## Run in cloudshell

```cmd
export ZONE=
```

```cmd
gcloud compute instances create gcelab \
--zone=$ZONE \
--machine-type=e2-medium \
--image-project=debian-cloud \
--image-family=debian-11 \
--tags=http-server
gcloud compute firewall-rules create allow-http \
--action=ALLOW \
--direction=INGRESS \
--rules=tcp:80 \
--source-ranges=0.0.0.0/0 \
--target-tags=http-server
gcloud compute instances create gcelab2 --machine-type e2-medium --zone=$ZONE
gcloud compute ssh gcelab --zone=$ZONE
```

### Y > ```enter``` > ```enter```

```cmd
sudo apt-get update
sudo apt-get install -y nginx
ps auwx | grep nginx
exit
```
