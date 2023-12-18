# airflow-setup

```
mkdir airflow
```
```
cd airflow && mkdir dags
```
```
sudo apt install python3-pip
```
```
airflow db init
```

```
airflow users create --username admin --password admin --firstname admin --lastname admin --role Admin --email admin@gmail.com
```

```
sudo nano /etc/systemd/system/airflow-scheduler.service
```
```

[Unit]
Description=Airflow Scheduler
After=network.target

[Service]
User=ddi
Group=ddi
Type=simple
ExecStart=/bin/sh -c './home/ddi/.local/bin/airflow scheduler > /home/ddi/airflow/logs/scheduler.log 2>&1'
Restart=on-failure
RestartSec=5s

[Install]
WantedBy=multi-user.target
```

```
sudo nano /etc/systemd/system/airflow-webserver.service
```

```
[Unit]
Description=Airflow Webserver
After=network.target

[Service]
User=ddi
Group=ddi
Type=simple
ExecStart=/bin/sh -c './home/ddi/.local/bin/airflow webserver -p 8080 > /home/ddi/airflow/logs/webserver.log 2>&1'
Restart=on-failure
RestartSec=5s

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
```

```
sudo systemctl start airflow-scheduler.service
sudo systemctl start airflow-webserver.service
```



