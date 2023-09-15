# GSP094

LAB LINK : https://www.cloudskillsboost.google/course_sessions/4892428/labs/377275

## Run in cloudshell

```cmd
sudo apt-get install -y virtualenv
python3 -m venv venv
source venv/bin/activate
pip install --upgrade google-cloud-pubsub
git clone https://github.com/googleapis/python-pubsub.git
cd python-pubsub/samples/snippets
python publisher.py $GOOGLE_CLOUD_PROJECT create MyTopic
python subscriber.py $GOOGLE_CLOUD_PROJECT create MyTopic MySub
```
