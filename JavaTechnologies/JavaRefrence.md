# pom.xml java compiler setting
##  
    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
    </properties>


# Maven Install & Path Setup
- First download & install maven from https://maven.apache.org/download.cgi
- Secondly setup below key, values in system environment variables.
- MAVEN_HOME : C:\apache-maven-3.8.6
- path : C:\apache-maven-3.8.6\bin

# Important Dependencies

##  Dependencies for Testing
### AssertJ
    <dependency>
      <groupId>org.assertj</groupId>
      <artifactId>assertj-core</artifactId>
      <version>3.10.0</version>
      <scope>test</scope>
    </dependency>

**Note:** - Field injection used for testing is slower then constructor injection.


