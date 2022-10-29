# Spring Cloud Stream
- it is a binding framework, which binds your code to the destination.
- spring cloud stream is a framework for building highly scalable event-driven microservices connected 
with shared messaging system like Kafka, RabbitMQ, Google PubSub.
- we can produces/process/consume data stream with any message broker (Kafka/RabbitMQ) without much 
configuration.



    ![](/images/spring/spring.drawio.png)
 

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

# Build.gradle file on the producer side.
	buildscript {
		ext {
			springBootVersion = '2.7.1'
			verifierVersion = '3.1.3'
		}
		repositories { mavenCentral() }
		dependencies {
			classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
			classpath "org.springframework.cloud:spring-cloud-contract-gradle-plugin:${verifierVersion}"
		}
	}

	apply plugin: 'groovy'
	apply plugin: 'java'
	apply plugin: 'eclipse'
	apply plugin: 'idea'
	//apply plugin: 'maven'
	apply plugin: 'org.springframework.boot'
	apply plugin: 'io.spring.dependency-management'
	apply plugin: 'spring-cloud-contract'


	group = 'com.example'
	version = '0.0.1-SNAPSHOT'
	bootJar {
		baseName = 'contract-rest-service'
	}
	sourceCompatibility = 1.8
	targetCompatibility = 1.8

	repositories { mavenCentral() }

	dependencies {
		implementation('org.springframework.boot:spring-boot-starter-web')
		testImplementation('org.springframework.boot:spring-boot-starter-test')
		testImplementation('org.springframework.cloud:spring-cloud-starter-contract-verifier')
	}

	dependencyManagement {
		imports {
			mavenBom "org.springframework.cloud:spring-cloud-dependencies:2021.0.3"
		}
	}

	contracts {
		packageWithBaseClasses = 'hello'
		baseClassMappings {
			baseClassMapping(".*hello.*", "hello.BaseClass")
		}
	}

	contractTest {
		useJUnitPlatform()
	}


# Base class for testing
	package hello;

	import org.junit.jupiter.api.BeforeEach;
	import org.mockito.Mockito;
	import org.springframework.beans.factory.annotation.Autowired;
	import org.springframework.boot.test.context.SpringBootTest;
	import org.springframework.boot.test.mock.mockito.MockBean;
	import org.springframework.test.context.junit4.SpringRunner;

	import io.restassured.module.mockmvc.RestAssuredMockMvc;

	@SpringBootTest(classes = ContractRestServiceApplication.class)
	public abstract class BaseClass {

	@Autowired PersonRestController personRestController;

	@MockBean PersonService personService;

	@BeforeEach public void setup() {
		RestAssuredMockMvc.standaloneSetup(personRestController);

		Mockito.when(personService.findPersonById(1L))
			.thenReturn(new Person(1L, "foo", "bee"));
	}

	}


# contract-verifier dependency
	testImplementation('org.springframework.cloud:spring-cloud-starter-contract-verifier')