# Build lifecycle basics
- ⚠️ **central pilar of Maven** ⚠️
  - === clearly defined the process, around a particular artifact (=== project) for
    - building it &
    - distributing it
  - requirements
    - learn small set of commands
- ⚠️ built-in build lifecycles ⚠️
  - `default`
    - handle your project deployment
    - === next sequential **ordered** [phases](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#a-build-lifecycle-is-made-up-of-phases)
      - `validate`
      - `initialize`
      - `generate-sources`
      - `process-sources`
      - `generate-resources`
      - `process-resources`
      - `compile`
      - `process-classes`
      - `generate-test-sources`
      - `process-test-sources`
      - `generate-test-resources`
      - `process-test-resources`
      - `test-compile`
      - `process-test-classes`
      - `test`
      - `prepare-package`
      - `package`
      - `pre-integration-test`
      - `integration-test`
      - `post-integration-test`
      - `verify`
      - `install`
      - `deploy`
  - `clean`
    - handle project cleaning
    - === next sequential ordered [phases](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#clean-lifecycle)
      - `pre-clean`
      - `clean`
      - `post-clean`
  - `site`
    - handle project’s web site creation
    - === next sequential ordered [phases](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#site-lifecycle)
      - `pre-site`
      - `site`
      - `post-site`
      - `site-deploy`
- === list of build phases / build lifecycle
  - → build phase := ⚠️ stage in the lifecycle ⚠️
    - can have bounded
      - 0 plugin goals
        - → NOT execute
      - ≥ 1 plugin goals
        - → ALL will be executed
  - phases are executed sequentially
  - phases / `pre-*`,`post-*`, or `process-*` → (normally) NOT available to be called from CL directly

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

---

# How to set up your project to use the build lifecycle ?
* TODO:

---

# Built-in lifecycle bindings
* TODO: