# GSP074

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892428/labs/377256 \
Video : https://youtu.be/rlBT45a9OG0

## Run in Cloudshell

```cmd
gsutil mb gs://$DEVSHELL_PROJECT_ID
curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output ada.jpg
gsutil cp ada.jpg gs://$DEVSHELL_PROJECT_ID
rm ada.jpg
gsutil cp -r gs://$DEVSHELL_PROJECT_ID/ada.jpg .
gsutil cp gs://$DEVSHELL_PROJECT_ID/ada.jpg gs://$DEVSHELL_PROJECT_ID/image-folder/
gsutil acl ch -u AllUsers:R gs://$DEVSHELL_PROJECT_ID/ada.jpg
```