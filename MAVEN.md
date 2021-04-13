# Maven 
Maven is a project lifecycle management tool that is based on POM (project object model)

# Configure Maven 
* Maven default configuration goes in `settings.xml` 
* Local Settings in `~/.m2/settings.xml` 
* Global Settings `${M2_HOME}/conf/settings.xml` 
  * Store Private Data `Usernames and Passwords` 
  * Configuration for mirror and proxy 
  * Global Profiles and Properties 

# Maven Lifecycle 
* validate - validate the project is correct and all necessary information is available
* compile - compile the source code of the project
* test - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
* package - take the compiled code and package it in its distributable format, such as a JAR.
* verify - run any checks on results of integration tests to ensure quality criteria are met
* install - install the package into the local repository, for use as a dependency in other projects locally
* deploy - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects

# Maven CLI 

| Maven Command 	| Description 	|
|-	|-	|
| mvn --version 	| Prints out the version of Maven you are running. 	|
| mvn clean 	| Clears the target directory into which Maven normally builds your project. 	|
| mvn package 	| Builds the project and packages the resulting JAR file into the target directory. 	|
| mvn package -Dmaven.test.skip=true 	| Builds the project and packages the resulting JAR file into the target directory - without running the unit tests during the build. 	|
| mvn clean package 	| Clears the target directory and Builds the project and packages the resulting JAR file into the target directory. 	|
| mvn clean package -Dmaven.test.skip=true 	| Clears the target directory and builds the project and packages the resulting JAR file into the target directory - without running the unit tests during the build. 	|
| mvn verify 	| Runs all integration tests found in the project. 	|
| mvn clean verify 	| Cleans the target directory, and runs all integration tests found in the project. 	|
| mvn install 	| Builds the project described by your Maven POM file and installs the resulting artifact (JAR) into your local Maven repository 	|
| mvn install -Dmaven.test.skip=true 	| Builds the project described by your Maven POM file without running unit tests, and installs the resulting artifact (JAR) into your local Maven repository 	|
| mvn clean install 	| Clears the target directory and builds the project described by your Maven POM file and installs the resulting artifact (JAR) into your local Maven repository 	|
| mvn clean install -Dmaven.test.skip=true 	| Clears the target directory and builds the project described by your Maven POM file without running unit tests, and installs the resulting artifact (JAR) into your local Maven repository 	|
| mvn dependency:copy-dependencies 	| Copies dependencies from remote Maven repositories to your local Maven repository. 	|
| mvn clean dependency:copy-dependencies 	| Cleans project and copies dependencies from remote Maven repositories to your local Maven repository. 	|
| mvn clean dependency:copy-dependencies package 	| Cleans project, copies dependencies from remote Maven repositories to your local Maven repository and packages your project. 	|
| mvn dependency:tree 	| Prints out the dependency tree for your project - based on the dependencies configured in the pom.xml file. 	|
| mvn dependency:tree -Dverbose 	| Prints out the dependency tree for your project - based on the dependencies configured in the pom.xml file. Includes repeated, transitive dependencies. 	|
| mvn dependency:tree -Dincludes=com.fasterxml.jackson.core 	| Prints out the dependencies from your project which depend on the com.fasterxml.jackson.core artifact. 	|
| mvn dependency:tree -Dverbose -Dincludes=com.fasterxml.jackson.core 	| Prints out the dependencies from your project which depend on the com.fasterxml.jackson.core artifact. Includes repeated, transitive dependencies. 	|
| mvn dependency:build-classpath 	| Prints out the classpath needed to run your project (application) based on the dependencies configured in the pom.xml file. 	|