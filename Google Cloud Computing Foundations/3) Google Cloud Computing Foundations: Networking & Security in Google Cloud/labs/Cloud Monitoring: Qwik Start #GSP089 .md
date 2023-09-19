# GSP089

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892518/labs/377223

## Run in cloudshell

```cmd
export ZONE=
```

```cmd
gcloud compute instances create lamp-1-vm \
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
gcloud compute ssh lamp-1-vm --zone=$ZONE
```
### Y > ```Enter``` > ```Enter```

```cmd
sudo apt-get update
sudo apt-get install apache2 php7.0
sudo service apache2 restart
curl -sSO https://dl.google.com/cloudagents/add-google-cloud-ops-agent-repo.sh
sudo bash add-google-cloud-ops-agent-repo.sh --also-install
sudo apt-get update
```
### Y > enter

## Now do 3 task 

### Search ```Uptime Check``` > ```Create Uptime Check```
### Protocol = ```HTTP```
### Instance = ```lamp-1-vm```
### Check Frequence = ```1 minute```
### Continue > Continue > title = ```Lamp Uptime Check``` > Test
- A Green tick will appear
### Create

## Now do 4 task 
### Search ```Alerting``` > ```+Create Policy``` 
### ```Select a metric``` > Disable ```Show only active resources & metrics``` > VM instance > Interface > ```Network traffic``` > Apply > Next 
### Threshold position = ```Above threshold``` > Threshold = ```500``` > Advanced Options > Retest window = ```1 min``` > Next
### Notification Channels > Manage Notification Channels
### Email > ADD NEW
### Email address = any email address > Display Name = Any name > save
### Go to previous tab
### Notification Channels > Refresh icon > Your Display Name > ok
### Alert Name = ```Inbound Traffic Alert```
### Next > Create Policy
