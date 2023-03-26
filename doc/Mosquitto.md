# Mosquitto MQTT

Mosquitto is an open-source message broker that implements the MQTT (Message Queuing Telemetry Transport) protocol. MQTT is a lightweight, publish-subscribe messaging protocol that is designed to be efficient, reliable, and easy to implement.

Mosquitto allows devices to publish and subscribe to topics, enabling them to exchange messages with each other in a distributed system. It supports various quality of service (QoS) levels, allowing devices to choose the appropriate level of reliability and performance for their needs.

## Install Broker

Install mosquitto and optional client tools:
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
Add password file to allow only authenticated user.


Restart Mosquitto
```bash
sudo systemctl restart mosquitto
systemctl status mosquitto
```

By default, Mosquitto will listen for incoming connections on port 1883. 

## Test the broker with pub/sub

Connect to the specified MQTT broker and subscribe to the specified topic filter. Any messages that are published to topics that match the filter will be received and displayed.

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

- `-h 192.168.1.2`: Specifies the IP address of the MQTT broker to connect to.
- `-p 1883`: Specifies the port number of the MQTT broker to connect to (1883 is the default port for non-encrypted MQTT).
- `-t livingroom/#`: Specifies the MQTT topic filter to subscribe to. In this example, it subscribes to all topics that start with `livingroom/`.
- `-u iot`: Specifies the username to use when connecting to the MQTT broker.
- `-P password`: Specifies the password to use when connecting to the MQTT broker.
- `-i testsubscriber`: Specifies the client identifier to use when connecting to the MQTT broker.
- `-v`: Enables verbose output, which displays the received messages along with other debug information.
- `-d`: Enables debug output


Connect to the specified MQTT broker and publish a message 
```bash
mosquitto_pub \
-h 192.168.1.2 \
-p 1883 \
-m "24.1" \
-t livingroom/temp \
-u iot \
-P password \
-i testpublisher \
-d
```

- `-h 192.168.1.2`: Specifies the IP address of the MQTT broker to connect to.
- `-p 1883`: Specifies the port number of the MQTT broker to connect to (1883 is the default port for non-encrypted MQTT).
- `-m "hello mqtt"`: Specifies the message payload to publish to the topic.
- `-t livingroom/temp`: Specifies the MQTT topic to publish the message to.
- `-u iot`: Specifies the username to use when connecting to the MQTT broker.
- `-P password`: Specifies the password to use when connecting to the MQTT broker.
- `-i testpublisher`: Specifies the client identifier to use when connecting to the MQTT broker.
- `-d`: Enables debug output

## QoS

MQTT uses a Quality of Service (QoS) level to define the guarantee of message delivery between the sender and the receiver. Mosquitto, being an MQTT broker, supports three QoS levels: QoS 0 (At most once), QoS 1 (At least once), and QoS 2 (Exactly once).

- QoS 0: At most once delivery means that the message is delivered once or not at all. There is no acknowledgment or retransmission of the message.
- QoS 1: At least once delivery means that the message is delivered at least once.
- QoS 2: Exactly once delivery means that the message is delivered exactly once and only once, regardless of network or system failures. This level of QoS involves a handshake between the broker and receiver to ensure that the message is only delivered once.

Example with Qos 1:
```bash
mosquitto_sub \
-h 192.168.1.2 \
-t livingroom/temp \
-q 1 \
-u iot \
-P password \
```

## Retain Flag
In MQTT, the "retain" flag is used to indicate whether the broker should retain the last message sent to a particular topic. When a client subscribes to a topic, and the flag is set, the broker will immediately send the last message that was published to the new subscriber. This allows clients to receive the most recent data even if they were not subscribed at the time of the message publication.