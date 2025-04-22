## Examples
* `mvn archetype:generate -DgroupId=com.example -DartifactId=cli -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`
  * Create the skeleton of the project
* Add the plugin skeleton indicated in the guide
* `mvn -X dependency:copy-dependencies package`
  * `-X`
    * option to run in debug mode
  * `dependency:copy-dependencies`
    * plugin goal
  * `package`
    * build phase
* `mvn verify`
  * you do NOT see the build phases itself normally, else plugins triggering behind -- 'maven-resources-plugin:resources', ' maven-compiler-plugin:compile', 'maven-resources-plugin:testResources', .. --
* TODO: Add an example for a project with subprojects
* `mvn pre-site`
  * nothing done
