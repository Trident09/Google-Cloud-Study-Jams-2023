# GSP151

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892428/labs/377260

## Run in cloudshell

```cmd
export ZONE=
```

```cmd
export REGION=${ZONE::-2}
gcloud sql instances create myinstance \
--database-version=MYSQL_8_0 \
--tier=db-n1-standard-4 \
--region=$REGION
gcloud sql connect myinstance --user=root
```

### Now press `Enter`

```cmd
CREATE DATABASE guestbook;
```
