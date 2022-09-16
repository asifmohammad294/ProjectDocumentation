# Spring Cloud Stream
- it is a binding framework, which binds your code to the destination.
- spring cloud stream is a framework for building highly scalable event-driven microservices connected 
with shared messaging system like Kafka, RabbitMQ, Google PubSub.
- we can produces/process/consume data stream with any message broker (Kafka/RabbitMQ) without much 
configuration.



    ![](./spring.drawio.png)
 

- The producer/processor/consumer simplified using java 8's functional interfaces.


# Official website for Spring-Cloud-Contract
- https://cloud.spring.io/spring-cloud-contract/reference/html/
- https://spring.io/guides/gs/contract-rest/

# Dependency & Plugin needed for Contract Testing

	- this dependency helps to write contracts like hints
    <dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-contract-verifier</artifactId>
			<scope>test</scope>
	</dependency>

	<!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-contract-verifier -->
	<dependency>
		<groupId>org.springframework.cloud</groupId>
		<artifactId>spring-cloud-starter-contract-verifier</artifactId>
		<version>3.1.2</version>
	</dependency>

**Note** : <dependencyManagement> is also required. 

    <plugin>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-contract-maven-plugin</artifactId>
				<version>2.1.0.BUILD-SNAPSHOT</version>
				<extensions>true</extensions>
				<configuration>
					<baseClassForTests>com.example.frauddetection.BaseClass
					</baseClassForTests>
				</configuration>
	</plugin>