# Python

### Integration Key

![](<../../.gitbook/assets/image (2).png>)

### API Key

![](<../../.gitbook/assets/image (3).png>)

### Python Script to create incidence

```
import json
import time
import requests # sudo pip3 install requests
import pypd # sudo pip3 install pypd
from pdpyras import APISession
import subprocess
import shutil

telegram_token = ""
telegram_chat_id = ""

# old version with library pypd

pypd.api_key = "u+GX4Wg-GVxEzZzGxyqg" # API Access Key
pypd.service_key = "9109b900f7c94e09d0c701995ea5f20e" # Integration Key, (Event API V2)
pypd.href = "https://dev-chandrodaya.pagerduty.com"
pypd.Event.create(data={
    'service_key': pypd.service_key,
    'event_type': 'trigger',
    'description': 'TEST: Validator down!!!',
    'contexts': [
          {
              'type': 'link',
              'href': pypd.href,
              'text': 'View on PD',
          },
    ],
})


# new version with library pdpyras

api_token = 'u+GX4Wg-GVxEzZzGxyqg'
session = APISession(api_token, default_from='dautruongtan@gmail.com')
payload = {
  "type": "incident",
  "title": "This is a test 4",
  "service": {"id": "PNQJSQS", "type": "service_reference"}
}
pd_incident = session.rpost("incidents", json=payload)


```

### library

{% embed url="https://github.com/PagerDuty/pdpyras" %}

