# Maven
## 1) Maven Introduction and Architecture
## 2) Maven Repository
## 3) Pom.xml dependency management
## 4) Maven Build Life Cycle
## 5) Multi-module projects 
## 6) Testing with maven

## 1) Maven Introduction and Architecture
>Maven is a Build Tool and Project Management Tool <br>
 Maven is a build automation tool used primarily for java projects

 >**What is Build Process?** <br>
* Keeping Resources Ready
* Arranging Resources in Various Folders
* Adding Libraries/Jars to classpath
* Compilation
* Execution
* Testing
* Packaging for release or deployment is continously required in project development 
  and Delivery Process

>>**NOTE** Keeping Our Project Ready for execution / Release is called Build Process
This involves multiple complicated and repetitive operations

>**Core Java Project**<br>
1)   Develop Java Resources and other files
2)   Keep them in  different folders
3)  Add Jars  / Libraries in Class Path
4)  Compilation
5)  Execution / Testing
6)  Packing the Project For Release (jar | war )

>**Unit Testing**  <br>
Programmers testing on their own piece of code is called Unit Testing

>>**Performing Build Process Activities manually is having lot of limitations**
1)  Remebering Complicated and Repetitive Operations is very tough
2)  We may mismatch order
3)  We may forget certian activities
4)  Doing multiple activities of Build Process Manually will waste our time and etc

Batch (.bat) :
------------------
Batch is given to combine related commands into single command (By using single command we can
automate the process)
>run.bat
*   cd T:
*   mkdir MyProject
*   copy source file into destination 
*   set path=......
*   set classpath=.....
*   javac -d . *.java
*   java <pakg>.<Main Class>

Limitations of Batch File:
--------------------------
1)  Conditional Execution is not possible
2)  We cannot create Dependency Among Operations
3)  Jars files must be added manually
4)  If one command fails in batch file , then next command will not execute
5)  It is not declarative(not self intelligent, ie. we need to tell eveything what to do)

To Overcome above limitations we got ANT Tool (Another Neat Tool):
-----------------------------------------------------------
* Same as batch file,but we can keep operations as conditional operations and we can maintain depedency among operations

To overcome above limitations with Batch and ANT Tools we got maven tool introduced with lot of advanced
features
-------------------------------------------------------

* ANT is just Build Tool .... 
* Maven is a Build Tool and Project Management Tool
* Maven is a build automation tool used primarily for java projects


Key Features of Maven
---------------------
1)  Maven tries to avoid as much configurations as possible , by choosing real worl default values and 
supplying project templates
2)  Download JAR Files Dynamically
3)  Can maintain multiple repositories having jar files ,plugins etc
4)  Provides Standard Project Directory Structures
5)  Alows to develop multiple module projects
6)  Has the capability to generate WAR[Web Application Archive]  ,JAR [Java Application Archive ] OR
  EAR [ Enterprise Application Archive ]
7)  Can Run Unit Tests and can generate unit test reports
8)  Can generate Project Documentation
9)  Can clean and install projects in local servers or remote servers

Maven Can be Used As
--------------------
 1) From CLI (Command Line Interface)
 2) From IDE (Integrated Development Environment] : STS ,ECLIPSE ,MYSCLIPSE ,NETBEANS

Official Maven WebSite
----------------------
maven.apache.org

## Maven Architecture
![Maven Architecure](maven+repositories.png "Title")



### Install Java and Maven
Update apt-get
---------------
*   sudo apt-get -v
*   sudo apt-get update -y

Add Java
--------
*   sudo dpkg --configure -a
*   sudo apt-get install openjdk-8-jdk -y
*   java -version

Simple Java
------------
*   nano Test.java
```java
public class Test{
public static void main(String[] args){
System.out.println("Welcome to Java");
}
}
```
*   compile and run
    *   javac Test.java
    *   java Test

*   Remove Java
    *   sudo apt-get remove openjdk-8-jdk -y

Adding Eclipse
---------------
*   sudo snap install --classic eclipse

*   Open an Eclipse
    *   To open eclipse Application : click application key,  type *eclipse* in search box and open 

### Adding Maven
*   sudo apt-get install maven
*   mvn -version

### Remove Maven
*   sudo apt-get remove maven

### from user home
*   nano .profile

### setting path for java
>**Syntax**<br>
JAVA_HOME=jdk_install_dir <br>
export JAVA_HOME <br>
PATH=$JAVA_HOME/bin:$PATH <br>
export PATH <br>

### find java and maven location
*   whereis jvm
	*   /usr/lib/jvm
*   cd /usr/lib/jvm
*   ls
	*   java-8-openjdk-amd64

```bash
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
export PATH
```

### from home
*   . .profile

```bash
suresh@testleaf:~$ echo $JAVA_HOME
/usr/lib/jvm/java-8-openjdk-amd64
```

### setting path for maven
```bash
suresh@testleaf:~$ mvn -version
Apache Maven 3.6.3
Maven home: /usr/share/maven
```

```bash
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export JAVA_HOME
MAVEN_HOME=/usr/share/maven
export MAVEN_HOME
PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH
```
### from home
*   . .profile

### Install Eclipse
*   sudo snap install --classic eclipse

Archetypes In Maven :
---------------------
Archetypes : Templates To Create Projects

1)  maven-archetype-quickstart : Standalone Projects
2)  maven-archetype-webapp     : Web Based Projects

Maven Standlone Project
-----------------------
1)  open command prompt
2)  mvn archetype:generate
3)  simple java code

```java
package com.suresh.demos;
public class App 
{
    public static void main( String[] args )
    {
        System.out.println( "Welcome to Maven" );
    }
}
```
```java
package com.suresh.demos;
public class Arithmetic 
{
    public static int add(int firstNumber,int secondNumber){
    return firstNumber+secondNumber;
    }
    public static void main( String[] args )
    {
        int addResult = Arithmetic.add(12,34);
        System.out.println("Add Result is "+addResult);
    }   
}
```
*   mvn compile
    *   Compiles .java files
    *   project-name-version.jar file


*   mvn clean
    *   Cleans the project  and deletes target folder

>>There is no special command to execute the code

*   mvn clean package
    *   Cleans the project and also creates jar file with latest code

*   java -cp target/Demo1-1.0.jar com.suresh.demos.Arithmetic

*   java -cp target/Demo1-1.0.jar com.suresh.demos.App
*   java -cp target/Demo2-1.0-SNAPSHOT.jar com.suresh.demos.App


## 2) Maven Repository
*   Repository is a small DB or folder which will hold items
*   A Repository in maven is used to hold artifacts and depedencies of various types
*   A Maven Repository is a place i.e Directory where all the project jars,plugins or any other project 
specific artifacts are stored and can be used by maven easily

*   There are 3 types of Repositories in Maven
  1) Central Repository ( Given By Apache Maven )
  2) Local Repository   (In Every Machine where maven is configured)
  3) Remote Repository  ( Given By Thrid Party Companies)

```
By Default For Every Maven Project one pom.xml [ Project Object File ] file is available
```

**Maven Repositories can hold** <br>
1) Jar Files / Library / Dependency 
2) Plugins ( Patch software used to provide additional functionality )

**In Maven Everything (Jar | Plugins | Projects ) is Identified with 3 details** <br>
1) artifactId ( Jar file name |  plugin name | project name)
2) groupId (company name)
3) version (verion of jar | plugin | project)

## 3) Pom.xml dependency management

![Maven Architecure](adding_dependencies.png "Title")]



## 4) Maven Build Life Cycle
---------------------------------
* Maven is based around the central concept of a build life cycle. It means the process for building and distributing artifact(project) is clearly defined

* There are 3 built in build life cycle 
  1) clean [3 phases]    : It handles project cleaning
  2) default [23 phases] : It handled project depolyment
  3) site [4 phases]     : It handles creation of Our Project Site Documentation

**Note** : Each lifecycle of a maven will have lots of phases.These phases already linked with plugins to
perform certain operations

Clean Life Cycle :

| Phase | Description|
|-------|------------|
| pre-clean | Execute processes needed prior to actual project cleaning|
| **clean** | Removes all files generated by previous build |
| post-clean | execute processes those are needed to finalize project cleaning |


Default Life Cycle :

1)  validate
    *   Validate the project is correct and all necessary information is available
2)  initialize         
    *   To initialize build state
3)  generate-sources   
*   Generate any source code for inclusion in compilation
4)  process-sources    
    *   Process source code
5)  generate-resources 
    *   generate resources for inclusion in package
6)  process-resources  
    * Copy and process the resources into destination directory ,ready for execution
7)  **compile**
    *   Compile the source code of tha project
8)  process-classes    
    *    Post process generated files from compilation
9)  generate-test-sources
    *   generate any test source doe  for inclusion in compilation
10) process-test-sources 
    *   Process test source code
11) generate-test-resources
    *   Create resources for testing
12) process-test-resources 
    *   copy and process resources into test destination directory
13) test-compile
    *   compile test source code into test destination directory
14) process-test-classes 
    *   post process generated files from test compilation
15) **test**
    *   run tests using suitable unit testing framework
16) prepare-package
    *   perform any necessary operations to prepeare before actual packaging
17) **package**
    *   Take the compiled code and package it in its distributable format such as jar
18) pre-integration-test
    *   perform actions required before integration tests are executed
19) integration-test
    *   process and deploy the pavkage if necessary into an environment where integration test can run
20) post-integration-test
    *   perform actions required after integration tests have been executed
21) **verify**
    *   run any checks to verify the package is valid and meets quality criteria
22) **install**
    *   install the package into local repository ,for use as dependency in other projects locally
23) **deploy**
    *   done in an integration or release environment ,copies the final package to the remote repository for sharing with other developers and projects

3)site Lifecycle [4 phases]:
1)  pre-site        
    *   execute processes needed prior to actual project site generation
2)  **site**
    *   generate project site generation
3)  post-site       
    *   execute processes needed to finalize site generation and to prepare for site deployment
4)  site-deploy     
    *   deploy the generated site documentation to the specified web server



## 5) Multi-module projects 
*   mvn archetype:generate -DgroupId=com.suresh.demos -DartifactId=Technology  -DarchetypeArtifactId=maven-archetype-quickstart 
*   cd Technology
*   mvn archetype:generate -DgroupId=com.suresh.demos -DartifactId=Java  -DarchetypeArtifactId=maven-archetype-quickstart
*   mvn archetype:generate -DgroupId=com.suresh.demos -DartifactId=Dotnet  -DarchetypeArtifactId=maven-archetype-quickstart 

*   mvn clean install




