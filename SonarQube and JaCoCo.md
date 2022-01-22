
# **Installation Guidelines**
# **SonarQube** 

<https://www.sonarqube.org/downloads/>
### SonarScanner
<https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/>
### Download Maven and Extract it
<https://maven.apache.org/download.cgi>    

[apache-maven-3.8.2-bin.zip](https://dlcdn.apache.org/maven/maven-3/3.8.2/binaries/apache-maven-3.8.2-bin.zip)

### Requirements  for SonarQube:
<https://docs.sonarqube.org/latest/requirements/requirements/>

### Install Sonarqube on Ubuntu 20.04:
<https://kifarunix.com/install-sonarqube-on-ubuntu/>

# **JaCoCo**
Code coverage is [a software metric](https://www.baeldung.com/cs/code-coverage) used to measure how many lines of our code are executed during automated tests.

**JaCoCo,** a code coverage reports generator for Java projects.
## **Maven Configuration**
### pom.xml
```xml
<plugin>

    <groupId>org.jacoco</groupId>

    <artifactId>jacoco-maven-plugin</artifactId>

    <version>0.7.7.201606060606</version>

    <executions>

        <execution>

            <goals>

                <goal>prepare-agent</goal>

            </goals>

        </execution>

        <execution>

            <id>report</id>

            <phase>prepare-package</phase>

            <goals>

                <goal>report</goal>

            </goals>

        </execution>

    </executions>

</plugin>
```

## **Code Coverage Reports - Demo**
### Code
```java
public boolean isPalindrome(String inputString) {

    if (inputString.length() == 0) {

        return true;

    } else {

        char firstChar = inputString.charAt(0);

        char lastChar = inputString.charAt(inputString.length() - 1);

        String mid = inputString.substring(1, inputString.length() - 1);

        return (firstChar == lastChar) && isPalindrome(mid);

    }

}
```
### Junit Test
```java
@Test

public void whenEmptyString\_thenAccept() {

    Palindrome palindromeTester = new Palindrome();

    assertTrue(palindromeTester.isPalindrome(""));

}
```
## Hint
>Running the test using JUnit will automatically set in motion the JaCoCo agent. It will create a coverage report in **binary format** in the target directory, *target/jacoco.exec.*

>Obviously we can't interpret the output single-handedly, but other tools and plugins can, e.g. [**Sonar Qube**](https://docs.sonarqube.org/latest/analysis/coverage/).

    The good news is that we can use the *jacoco:report* goal in order to generate readable code coverage reports in several formats, like HTML, CSV, and XML.

For example, now we can take a look at the *target/site/jacoco/index.html* page to see what the generated report looks like:


- **Red diamond** means that no branches have been exercised during the test phase.
- **Yellow diamond** shows that the code is partially covered – some branches have not been exercised.
- **Green diamond** means that all branches have been exercised during the test.

The same color code applies to the background color, but for lines coverage.

JaCoCo mainly provides three important metrics:

- **Lines coverage** reflects the amount of code that has been exercised based on the number of Java byte code instructions called by the tests.
- **Branches coverage** shows the percent of exercised branches in the code, typically related to *if/else* and *switch* statements.
- **Cyclomatic complexity** reflects the complexity of code by giving the number of paths needed to cover all the possible paths in a code through linear combination.


Now that we know a bit about how JaCoCo works, let's improve our code coverage score.

In order to achieve 100% code coverage, we need to introduce tests that cover the missing parts shown in the initial report:

```java
@Test

public void whenPalindromthenAccept() {

    Palindrome palindromeTester = **new** Palindrome();

    assertTrue(palindromeTester.isPalindrome("noon"));
}




@Test

public void whenNearPalindromthanReject(){
    Palindrome palindromeTester = new Palindrome();
    assertFalse(palindromeTester.isPalindrome("neon"));
}
```


## **Generage HTML Report**
```xml
<build>

        <plugins>

            <plugin>

                <groupId>org.apache.maven.plugins</groupId>

                <artifactId>maven-compiler-plugin</artifactId>

                <version>3.1</version>

                <configuration>

                    <source>${jdk.version}</source>

                    <target>${jdk.version}</target>

                    <encoding>${project.build.sourceEncoding}</encoding>

                </configuration>

            </plugin>

            <plugin>

                <groupId>org.jacoco</groupId>

                <artifactId>jacoco-maven-plugin</artifactId>

                <version>0.7.6.201602180812</version>

                <executions>
                    <!-- Prepares the property pointing to the JaCoCo runtime agent which

                        is passed as VM argument when Maven the Surefire plugin is executed. -->

                    <execution>

                        <id>pre-unit-test</id>

                        <goals>

                            <goal>prepare-agent</goal>

                        </goals>

                        <configuration>

                            <!-- Sets the name of the property containing the settings for JaCoCo

                                runtime agent. -->

                            <propertyName>surefireArgLine</propertyName>

                        </configuration>

                    </execution>

                    <!-- Ensures that the code coverage report for unit tests is created

                        after unit tests have been run. -->

                    <execution>

                        <id>post-unit-test</id>

                        <phase>test</phase>

                        <goals>

                            <goal>report</goal>

                        </goals>

                        <configuration>

                            <!-- Sets the output directory for the code coverage report. -->

                            <outputDirectory>${project.reporting.outputDirectory}/jacoco-ut</outputDirectory>

                        </configuration>

                    </execution>

                </executions>

            </plugin>

            <!-- Used for unit tests -->

            <plugin>

                <groupId>org.apache.maven.plugins</groupId>

                <artifactId>maven-surefire-plugin</artifactId>

                <version>2.19.1</version>

                <configuration>

                    <!-- Sets the VM argument line used when unit tests are run. -->

                    <argLine>${surefireArgLine}</argLine>

                </configuration>

            </plugin>

        </plugins>

    </build>
```
## **To add min. code coverage**
In a real world project, as developments go further, we need to keep track of the code coverage score.

JaCoCo offers a simple way of declaring **minimum requirements** that should be met, otherwise the build will fail.

We can do that by adding the following *check* goal in our *pom.xml* file:
```xml 
<execution>
    <id>jacoco-check</id>
    <goals>
        <goal>check</goal>
    </goals>
    <configuration>
        <rules>
            <rule>
                <element>PACKAGE</element>
                <limits>
                    <limit>
                        <counter>LINE</counter>
                        <value>COVEREDRATIO</value>
                        <minimum>0.50</minimum>
                    </limit>
                </limits>
            </rule>
        </rules>
    </configuration>
</execution>
```
As we can see, we're limiting the minimum score for lines coverage to 50%.


# **SonarQube**
## Code Quality and Code Security
## Download SonarQube and Extract it.

### Download Link
<https://www.sonarqube.org/downloads/>

(SonarQube 8.9.2 LTS (July 2021) – community edition
# Install from Zip file
1. [Download](https://www.sonarqube.org/downloads/) the SonarQube Community Edition zip file.
1. As a non-root user, unzip it, let's say in C:\sonarqube or /opt/sonarqube.
1. As a non-root user, start the SonarQube Server:
1. On Windows, execute:
1. C:\sonarqube\bin\windows-x86-64\StartSonar.bat
1. On other operating systems, as a non-root user execute:

/opt/sonarqube/bin/[OS]/sonar.sh start
# Install from Doccer Image
Find the Community Edition Docker image on [Docker Hub](https://hub.docker.com/_/sonarqube/).

1. Start the server by running:

$ docker run -d --name sonarqube -e SONAR\_ES\_BOOTSTRAP\_CHECKS\_DISABLE=true -p 9000:9000 sonarqube:latest
### Requirements
<https://docs.sonarqube.org/latest/requirements/requirements/>

(Min. java version – 11)
### Open  in Web Browser
Once your instance is up and running, Log in to [http://localhost:9000](http://localhost:9000/) using System Administrator credentials:

- login: admin
- password: admin


### Download SonarScanner  and Extract it.
<https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/>

### Download Maven and Extract it.
<https://maven.apache.org/download.cgi>     -    [apache-maven-3.8.2-bin.zip](https://dlcdn.apache.org/maven/maven-3/3.8.2/binaries/apache-maven-3.8.2-bin.zip)

### Setting Path:
**User Variable:**

JAVA\_HOME  - C:\Program Files\Java\jdk-11.0.12

MAVEN\_HOME - C:\Program Files\apache-maven-3.8.2

M2\_HOME - C:\Program Files\apache-maven-3.8.2

SONAR\_HOME - E:\Suresh\OT\W4\sonarqube-8.9.2.46101\sonarqube-8.9.2.46101\bin\windows-x86-64

SONAR\_SCANNER\_HOME - E:\Suresh\OT\W4\sonar-scanner-cli-4.6.2.2472-windows\sonar-scanner-4.6.2.2472-windows

User Variable – Path

%JAVA\_HOME%

%MAVEN\_HOME%\bin

%M2\_HOME%\bin

%SONAR\_HOME%

%SONAR\_SCANNER\_HOME%\bin



# SonarQube Demo1

## *FirstSonar.java*
```java
package com.suresh.sonar.demos;
public class FirstSonarJava {

	public static final String abc="";
	public static String [] strings1 = {"first","second"};
	
	
	public static void main(String[] args) {
		String MayBeNull = null;
		System.out.println("Hello SonarQube "+MayBeNull);
		 
		for (int i = 10; i < 15; i++) { 
			System.out.println("Loop not true even once");
		}	
	} 
}
```

# sonar-project.properties
## Required metadata
```xml
sonar.projectKey=java-sonar-runner-simple
sonar.projectName=Simple Java project analyzed with the SonarQube Runner
sonar.projectVersion=1.0
```
## Comma-separated paths to directories with sources (required)
```
sonar.sources=src
```
## Language
```
sonar.language=java
```

## Encoding of the source files
```
sonar.sourceEncoding=UTF-8
```

## *Start SonarQube*
powershell / command prompt:

>PS E:\Suresh\ot\w4\sonarqube-8.9.2.46101\sonarqube-8.9.2.46101\bin\windows-x86-64> 

	StartSonar.bat

>In Project Location

PS E:\Suresh\OT\Java Demos\SonarScannerDemo1>    

	sonar-scanner.bat

>[http://localhost:9000](http://localhost:9000/) 


### SonarQube Demo2
#### *maven - pom.xml => properties*
```xml
	<properties>

		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>

		<maven.compiler.source>11</maven.compiler.source>

		<maven.compiler.target>11</maven.compiler.target>

		<java.version>11</java.version>

	</properties>
```

#### *setting.xml:*
```xml
<settings>

    <pluginGroups>

        <pluginGroup>org.sonarsource.scanner.maven</pluginGroup>

    </pluginGroups>

    <profiles>

        <profile>

            <id>sonar</id>

            <activation>

                <activeByDefault>true</activeByDefault>

            </activation>

            <properties>

                <!-- Optional URL to server. Default value is http://localhost:9000 -->

                <sonar.host.url>

                  http://localhost:9000

                </sonar.host.url>

            </properties>

        </profile>

     </profiles>

</settings>
```


## To send report to sonarqube
In Project Location:

	mvn clean install

	mvn sonar:sonar

    Open Sonarqube in browser

