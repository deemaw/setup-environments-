
# STEP 1: GET KAFKA
Download the latest Kafka release and extract it:

$ tar -xzf kafka_2.13-2.7.0.tgz
$ cd kafka_2.13-2.7.0

# STEP 2: START THE KAFKA ENVIRONMENT
NOTE: Your local environment must have Java 8+ installed.

Run the following commands in order to start all services in the correct order:

# Start the ZooKeeper service
# Note: Soon, ZooKeeper will no longer be required by Apache Kafka.
$ bin/zookeeper-server-start.sh config/zookeeper.properties
Open another terminal session and run:

# Start the Kafka broker service
$ bin/kafka-server-start.sh config/server.properties

# STEP 3: CREATE A TOPIC TO STORE YOUR EVENTS

$ bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092

$ bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092

# STEP 4: WRITE SOME EVENTS INTO THE TOPIC

$ bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092

# STEP 5: READ THE EVENTS

$ bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092

# STEP 6: TERMINATE THE KAFKA ENVIRONMENT
Now that you reached the end of the quickstart, feel free to tear down the Kafka environment—or continue playing around.

Stop the producer and consumer clients with Ctrl-C, if you haven't done so already.
Stop the Kafka broker with Ctrl-C.
Lastly, stop the ZooKeeper server with Ctrl-C.
If you also want to delete any data of your local Kafka environment including any events you have created along the way, run the command:

$ rm -rf /tmp/kafka-logs /tmp/zookeeper