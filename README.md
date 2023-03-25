# raspberrypi-home-server

## Mosquitto MQTT Broker

Install server and client:
```bash
sudo apt install mosquitto mosquitto-clients -y
sudo systemctl enable mosquitto.service
```

Create a user with name iot for Mosquitto and enter password when promted.
```console
$ sudo mosquitto_passwd -c /etc/mosquitto/passwd iot
Password: 
Reenter password: 
```

Edit /etc/mosquitto/mosquitto.conf
```
per_listener_settings true

pid_file /var/run/mosquitto.pid

persistence true
persistence_location /var/lib/mosquitto/

log_dest file /var/log/mosquitto/mosquitto.log

include_dir /etc/mosquitto/conf.d

allow_anonymous false
password_file /etc/mosquitto/passwd
```
Add password file to enable only authenticated user.


Restart Mosquitto
```bash
sudo systemctl restart mosquitto
systemctl status mosquitto
```

Subscribe to livingroom topics:
```bash
mosquitto_sub \
-h 192.168.1.2 \
-p 1883 \
-t livingroom/# \
-u iot \
-P password \
-i testsubscriber \
-v \
-d
```

Publish test data to livingroom/temp topic:
```bash
mosquitto_pub \
-h 192.168.1.2 \
-p 1883 \
-m "hello mqtt" \
-t livingroom/temp \
-u iot \
-P password \
-i testpublisher \
-d
```