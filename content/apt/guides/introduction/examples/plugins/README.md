## Examples
- `mvn archetype:generate -DgroupId=com.example -DartifactId=plugins -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`
  - Create the skeleton of the project
- `mvn help:describe -Dplugin=org.apache.maven.plugins:maven-compiler-plugin`
  - Previously added the plugin 'org.apache.maven.plugins.maven-help-plugin'
  - `help:describe`
    - plugin goal / 
      - -- provides -- information about the plugin requested
    - Check the logs of execution of the command / verify that it's -- NOT bounded to -- build phase
      - == standalone goal
- `mvn -X compile`
  - Previously added the plugin 'org.apache.maven.plugins.maven-compiler-plugin'
  - Check in the logs of execution of the command that
    - `compile` build phase is indeed executed
- `mvn clean dependency:copy-dependencies package`
  - Check the execution order
    - `clean`
      - executed -- through -- the plugin [maven-clean-plugin](https://github.com/apache/maven-clean-plugin) 
      - refers to `clean` build phase -> ALL the previous build phases executed
    - `dependency:copy-dependencies`
      - executed -- through -- [maven-dependency-plugin](https://github.com/apache/maven-dependency-plugin)
      - plugin's goal 
    - `package`
      - executed -- through -- [maven-jar-plugin](https://github.com/apache/maven-jar-plugin)
      - refers to `package` build phase -> ALL the previous build phases executed

---

- TODO: