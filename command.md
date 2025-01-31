
 # Kafka with ZooKeeper

Run the following commands in order to start all services in the correct order:

## Start the ZooKeeper service
```
 bin/zookeeper-server-start.sh config/zookeeper.properties
```

Open another terminal session and run:

## Start the Kafka broker service
```
 bin/kafka-server-start.sh config/server.properties
```

Once all services have successfully launched, you will have a basic Kafka environment running and ready to use.


To get started with **Apache Kafka** CLI commands, you'll need to have Kafka installed and set up on your system. Here’s a guide to learning the basic Kafka CLI commands for working with topics, producers, and consumers.

### 1. **Create, List, and Delete Topics**

#### **Create a Topic:**
To create a topic in Kafka, use the `kafka-topics.sh` command. Here’s the syntax:

```bash
kafka-topics.sh --create --topic <topic-name> --bootstrap-server <broker-list> --partitions <num-partitions> --replication-factor <num-replicas>
```

Example:
```bash
kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1
```

- `--topic`: The name of the topic.
- `--bootstrap-server`: The Kafka broker list (usually `localhost:9092` for local setups).
- `--partitions`: Number of partitions for the topic.
- `--replication-factor`: Number of replicas for the topic.

#### **List Topics:**
To list all available topics, use the `--list` flag with `kafka-topics.sh`:

```bash
kafka-topics.sh --list --bootstrap-server <broker-list>
```

Example:
```bash
kafka-topics.sh --list --bootstrap-server localhost:9092
```

#### **Delete a Topic:**
To delete a topic, use the `--delete` flag:

```bash
kafka-topics.sh --delete --topic <topic-name> --bootstrap-server <broker-list>
```

Example:
```bash
kafka-topics.sh --delete --topic test-topic --bootstrap-server localhost:9092
```

### 2. **Send Data using Producer**

A Kafka producer sends messages to a topic. Use the `kafka-console-producer.sh` command to send data to a topic from the command line.

#### **Basic Command:**
```bash
kafka-console-producer.sh --broker-list <broker-list> --topic <topic-name>
```

Example:
```bash
kafka-console-producer.sh --broker-list localhost:9092 --topic test-topic
```

Once this command is executed, you can start typing messages into the terminal. Each line you type will be sent as a message to the `test-topic` topic.

#### **Sending Messages to Kafka:**
Type messages, and press **Enter** after each message to send it. For example:

```
Hello, Kafka!
Another message
```

### 3. **Consume Data using Consumer**

A Kafka consumer reads messages from a Kafka topic. Use the `kafka-console-consumer.sh` command to consume messages from a topic.

#### **Basic Command:**
```bash
kafka-console-consumer.sh --bootstrap-server <broker-list> --topic <topic-name> --from-beginning
```

Example:
```bash
kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test-topic --from-beginning
```

- `--from-beginning`: Ensures that the consumer reads all messages from the beginning, not just new ones.

#### **Consume Messages:**
Once executed, you will see the messages that were produced to the topic, such as:

```
Hello, Kafka!
Another message
```

### Summary of Commands:

- **Create Topic:**
  ```bash
  kafka-topics.sh --create --topic <topic-name> --bootstrap-server <broker-list> --partitions <num-partitions> --replication-factor <num-replicas>
  ```
  
- **List Topics:**
  ```bash
  kafka-topics.sh --list --bootstrap-server <broker-list>
  ```
  
- **Delete Topic:**
  ```bash
  kafka-topics.sh --delete --topic <topic-name> --bootstrap-server <broker-list>
  ```
  
- **Producer (Send Data):**
  ```bash
  kafka-console-producer.sh --broker-list <broker-list> --topic <topic-name>
  ```
  
- **Consumer (Receive Data):**
  ```bash
  kafka-console-consumer.sh --bootstrap-server <broker-list> --topic <topic-name> --from-beginning
  ```

---

This should get you started with Kafka CLI commands. If you need help setting up Kafka or want to go deeper into any of these commands, feel free to ask!
