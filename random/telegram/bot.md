# Bot

### Reference:

{% embed url="https://sbcode.net/grafana/telegram-bot/" %}

### Get BOT API Token

#### 1) Search @BotFather&#x20;

#### 2) Start conversation

#### 3) Enter \*/newbot\*

#### 4) Give a name

#### 5) give username

#### 6 ) Get BOT API Token



![](<../../.gitbook/assets/image (4).png>)

### Get Chat ID

1\) Create a new Group

2\) Add bot&#x20;

3\) Send one message to the bot

```
#example 
Hello @Orai_ChandraBot
```

4\) execute this call in the browser: **https://api.telegram.org/bot**_**XXX:YYY**_**/getUpdates** (replace the XXX:YYY with the **BOT API token** you just got from Telegram)

```
https://api.telegram.org/bot1949258182:AAEVqzoh9GmiUFhju8Q0gnYzWeJGPenzSA8/getUpdates
```

5\) Get the Chat ID

### Bot python script

```
import json
import time
import requests # sudo pip3 install requests
import pypd # sudo pip3 install pypd
import subprocess
import shutil

telegram_token = "XXXXXX:YYYYYYYYYYYYYYYYYYYY"
telegram_chat_id = "-123214343"


alarm_content="Hello from OraiBot!"
requestURL = "https://api.telegram.org/bot" + str(telegram_token) + "/sendMessage?chat_id=" + telegram_chat_id + "&text="
requestURL = requestURL + str(alarm_content)
response = requests.get(requestURL, timeout=1)
```



