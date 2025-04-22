## Examples
* `mvn archetype:generate -DgroupId=com.example -DartifactId=build-lifecycle -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`
  * Create the skeleton of the project
* Command to list all the build phases / built-in build lifecycle
  * Attempt1: `mvn help:describe -Dcmd=lifecycle` OR `mvn help:describe -Dcmd=default`
    * 'lifecycle' NOR 'default' do NOT exist
  * Attempt2: `mvn help:describe -Dcmd=validate` -- `mvn help:describe -Dcmd=SomeBuildPhase` --
    * Other way around. You provide a build phase and link to a build phase
  * Attempt3: `mvn help:describe`
    * invalid
  * Attempt3: `mvn -X`
    * JUST display the available build phases, but NOT linked to build lifecycles
  * Attempt4: `mvn buildplan:list`
    * display the link to build phases -- to -- plugin goals
  * Attempt5: 'fr.jcgay.maven.plugins:buildplan-maven-plugin'
    * `mvn fr.jcgay.maven.plugins:buildplan-maven-plugin:list`
      * list plugin goals | execution order
    * `mvn fr.jcgay.maven.plugins:buildplan-maven-plugin:list-phase`
      * group plugin goals / build phase 
    * `mvn fr.jcgay.maven.plugins:buildplan-maven-plugin:list-plugin`
      * group plugin goals / plugin
  * Solution: `mvn -X validate` -- `mvn -X SomeBuildPhase` --
    * Check in the logs the build phase / built-in build lifecycle
* Check that build phases -- can be bounded or NOT to -- plugin goals
  * `mvn help:describe -Dcmd=compile`
    * -- bounded to -- 'maven-compiler-plugin:compile'
  * `mvn help:describe -Dcmd=initialize`
    * -- NOT bounded to -- a plugin
* Phases / have prefixes -> NOT available to be called directly from CL
  * `mvn pre-integration-test` OR `mvn post-integration-test` 
    * exception
  * `mvn pre-clean` OR `mvn pre-site`
    * NOTHING done
* Check that
  * 'jacoco-maven-plugin' has goals / -- bounded to -- 'pre-integration-test'
    * `mvn help:describe -Dplugin=org.jacoco:jacoco-maven-plugin`
      * check that the plugin goal 'prepare-agent-integration' is bounded to
  * 'cargo-maven3-plugin' & 'tomcat7-maven-plugin' & 'docker-maven-plugin' prepare the integration test container environment
    * `mvn help:describe -Dplugin=org.codehaus.cargo:cargo-maven3-plugin`
      * Problem: Which goal is bounded ?
        * Solution: TODO:
    * `mvn help:describe -Dplugin=org.apache.tomcat.maven:tomcat7-maven-plugin`
      * you can check that the goal 'shutdown' seems to be bounded
    * `mvn help:describe -Dplugin=io.fabric8:docker-maven-plugin`
      * you can check that the goal 'stop' seems to be bounded
  * 'maven-failsafe-plugin' bind the goals 'integration-test' & 'verify'
    * `mvn help:describe -Dplugin=org.apache.maven.plugins:maven-failsafe-plugin`
      * you can check that the goal 'integration-test' & 'verify' exist

* TODO: