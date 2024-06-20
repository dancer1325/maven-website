# Goal
* Check that you can specify a dependency for a build plugin

## How was created?
* `mvn archetype:generate -DgroupId=com.build -DartifactId=dependencies -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`

## How to check the plugin using the dependency?
* `mvn -X org.apache.maven.plugins:maven-antrun-plugin:run -Dexec.executable="echo" -Dexec.args="executing maven-antrun-plugin"`
  * Forces the execution of the plugin & check in the console, the use of "org.apache.ant:ant:jar:1.7.1"
  * Attempts (previous to check this)
    * Attempt1: `mvn clean compile` & `mvn -X clean compile`
    * Attempt2: `mvn dependency:tree -Dverbose -Dincludes=org.apache.ant:ant` & `mvn dependency:tree -Dverbose -Dincludes=org.apache.ant` & `mvn dependency:tree -Dverbose`

## Notes
* `mvn help:effective-pom`
  * Check the effective POM applied
    * == also the default ones appear