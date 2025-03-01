# Slack Integration
This script fetches events from vRealize Network Insight and sends them to Slack.

## Requirements
As a preparation for using this script, you need to create a slack application at: https://api.slack.com/apps?new_app=1
In your slack app, choose "Incoming Webhooks" feature, which will generate a webhook URL for your channel to which the messages should be sent.
Copy this URL and pass it as a parameter to the script SlackHelper.py as shown below.

Apart from the webhook configuration, please make sure to have the following:

* Python 2.7 or above
* Linux server with crontab installed (or a Windows equivalent)

## Usage
```
python SlackHelper.py -d <IP/FQDN of platform> -u <username> -p <password> -s <Slack webhook URL>
```

e.g.
```
python SlackHelper.py -d vrni.lab.local -u admin@local -p SomePassword -s https://hooks.slack.com/services/XXXXXJSX3XX/B03333QGXSA/eGqlQWxs1EGiIm6RGssuisbT
````

Using above command, setup a cron job for every five minutes:
```
*/5 * * * * python SlackHelper.py -d vrni.lab.local -u admin@local -p SomePassword -s https://hooks.slack.com/services/XXXXXJSX3XX/B03333QGXSA/eGqlQWxs1EGiIm6RGssuisbT
````

The script will then pull the events of 5 minutes, format them for slack, and send it to slack.