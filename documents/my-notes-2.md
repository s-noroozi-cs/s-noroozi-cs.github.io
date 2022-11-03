# Apache Storm
* Apache Storm is a processing engine in big data used for real-time analytics and computation. 
* It is easily available open-source and distributed data framework.
* It is hugely scalable and faults tolerance, embedded with assured processing and mechanism of data.

# Error Handling via Dead Letter Queue in Apache Kafka
* The Dead Letter Queue (DLQ) is a service implementation within a messaging system or data streaming platform to store messages that are not processed successfully. Instead of passively dumping the message, the system moves it to a Dead Letter Queue.
* The main reason for putting a message into a DLQ in Kafka is usually a bad message format or invalid/missing message content.
  * An application error occurs if a value is expected to be an Integer, but the producer sends a String. 
  * In more dynamic environments, a “Topic does not exist” exception might be another error why the message cannot be delivered.
* The Kafka architecture does not support DLQ within the broker.
* The true decoupling of the data streaming platform enables a much more clean domain-driven design. Each microservice or application implements its logic with its own choice of technology, communication paradigm, and error handling.
* In traditional middleware and message queues, the broker provides this logic. The consequence is worse scalability and less flexibility in the domains, as only the middleware team can implement integration logic.
* The source code for a Dead Letter Queue implementation contains a try-cath block to handle expected or unexpected exceptions. The message is processed if no error occurs. Send the message to a dedicated DLQ Kafka topic if any exception occurs.
* The failure cause should be added to the header of the Kafka message. The key and value should not be changed so that future re-processing and failure analysis of historical events are straightforward.
* Kafka Connect is the integration framework of Kafka
  * configuration options 
    * errors.tolerance=all
    * errors.deadletterqueue.topic.name=my_dlq
* When NOT to use a Dead Letter Queue in Kafka?
  * DLQ for backpressure handling?
  * DLQ for connection failures?

