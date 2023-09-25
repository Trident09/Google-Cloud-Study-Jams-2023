# GSP119

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4893841/labs/403559 \
Video : https://youtu.be/xVDqSvm29So

## Run in cloudshell

```cmd
gcloud compute ssh linux-instance
```

### Press `y` , `ENTER` > `ENTER` > `ENTER` > `n`, `ENTER`

```cmd
export API_KEY=
```

### Get API KEY from `Navigation menu` > `APIs & services` > `Credentials` > `Create credentials` > `API key`

```cmd
cat > request.json <<EOF
{
  "config": {
      "encoding":"FLAC",
      "languageCode": "en-US"
  },
  "audio": {
      "uri":"gs://cloud-samples-tests/speech/brooklyn.flac"
  }
}
EOF
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json
```
