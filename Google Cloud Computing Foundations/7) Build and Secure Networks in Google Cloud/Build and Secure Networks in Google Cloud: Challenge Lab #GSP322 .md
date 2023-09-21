# GSP322

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4893768/labs/404067

## Run in Cloudshell
```cmd
SSH_IAP_Network_tag=
```
```cmd
SSH_Internal_Network_tag=
```
```cmd
HTTP_Network_Tag=
```
### Search ```Vm instance``` > Copy the Zone 
```cmd
ZONE=
```
```cmd
gcloud compute firewall-rules delete open-access --quiet
gcloud compute instances add-tags bastion --tags=$SSH_IAP_Network_tag --zone=$ZONE
gcloud compute instances start bastion --zone=$ZONE
gcloud compute firewall-rules create trident \
    --action=ALLOW \
    --network=acme-vpc \
    --rules=tcp:22 \
    --source-ranges=35.235.240.0/20 \
    --target-tags=$SSH_IAP_Network_tag \
    --description="Allow SSH from IAP service" 
gcloud compute instances add-tags bastion --tags=$SSH_IAP_Network_tag --zone=$ZONE
gcloud compute firewall-rules create gcptrident \
    --action=ALLOW \
    --network=acme-vpc \
    --rules=tcp:80 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=$HTTP_Network_Tag \
    --description="gcptrident"
gcloud compute instances add-tags juice-shop --tags=$HTTP_Network_Tag --zone=$ZONE
gcloud compute firewall-rules create gccftrident \
    --action=ALLOW \
    --network=acme-vpc \
    --rules=tcp:22 \
    --source-ranges=192.168.10.0/24 \
    --target-tags=$SSH_Internal_Network_tag \
    --description="GCCFTrident"
gcloud compute instances add-tags juice-shop --tags=$SSH_Internal_Network_tag --zone=$ZONE
gcloud compute ssh bastion --zone=$ZONE --quiet
```
```cmd
gcloud compute ssh juice-shop --internal-ip
```
### Y > ```enter``` > ```enter``` > y > ```enter```
