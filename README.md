# create-linux-service-python
create linux service python

## instal systemd
```
sudo apt-get install -y systemd
```

```
systemd --version
```

## create python file demo
```
vi /root/test/test.py
```

```
import time
from datetime import datetime
while True:
    print("z")
    with open("/root/test/timestamp.txt", "a") as f:
        f.write("The current timestamp is: " + str(datetime.now())+"\n")
        f.close()
    time.sleep(3)
```


## create file service
```
vi /etc/systemd/system/test.service
```

```
[Unit]
Description=My test service
After=multi-user.target

[Service]
Type=simple
Restart=always
ExecStart=/usr/bin/python3 /root/test/test.py

[Install]
WantedBy=multi-user.target
```


## start service
```
sudo systemctl daemon-reload
```

enable service while restart pc
```
sudo systemctl enable test.service
```

start service
```
sudo systemctl start test.service
```

stop service
```
sudo systemctl stop test.service
```

restart service
```
sudo systemctl restart test.service
```
