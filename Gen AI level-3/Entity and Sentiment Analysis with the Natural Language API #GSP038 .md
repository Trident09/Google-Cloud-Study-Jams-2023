# GSP038

LAB LINK : https://www.cloudskillsboost.google/games/4422/labs/28607
Video : https://youtu.be/Or46jl6yInw

## CREATE AN API_KEY > APIs & Services > Credentials > Create Credentials > API key

## Run in cloudshell

```cmd
gcloud beta compute ssh  linux-instance
```

### Press Y Enter > Enter > Enter > Press N Enter

```cmd
gcloud services enable apikeys.googleapis.com
gcloud alpha services api-keys create --display-name="CloudTrident"
KEY_NAME=$(gcloud alpha services api-keys list --format="value(name)" --filter "displayName=CloudTrident")
API_KEY=$(gcloud alpha services api-keys get-key-string $KEY_NAME --format="value(keyString)")
echo $API_KEY
touch request.json
tee request.json <<EOF
{
  "document":{
    "type":"PLAIN_TEXT",
    "content":"Joanne Rowling, who writes under the pen names J. K. Rowling and Robert Galbraith, is a British novelist and screenwriter who wrote the Harry Potter fantasy series."
  },
  "encodingType":"UTF8"
}
EOF
cat request.json
curl "https://language.googleapis.com/v1/documents:analyzeEntities?key=${API_KEY}" -s -X POST -H "Content-Type: application/json" --data-binary @request.json > result.json
cat result.json
```
