# Error Handling via Dead Letter Queue in Apache Kafka
* Case Studies for a Dead Letter Queue in Kafka
  * Uber – Building Reliable Reprocessing and Dead Letter Queues
    * In distributed systems, retries are inevitable. 
      * From network errors to replication issues and even outages in downstream dependencies, 
      * services operating at a massive scale must be prepared to encounter, 
      * identify, 
      * and handle failure as gracefully as possible.
  * Given the scope and pace at which Uber operates, its systems must be fault-tolerant and uncompromising when failing intelligently. 
  * Uber leverages Apache Kafka for various use cases at an extreme scale to accomplish this.
  * summary: one topic for processing, n topic to retry failed and at final one dlq topic
