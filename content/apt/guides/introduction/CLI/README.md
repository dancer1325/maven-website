* `mvn [options] [<goal(s)>] [<phase(s)>]`
  * options available
    * Check [here](https://maven.apache.org/ref/3.6.1/maven-embedder/cli.html)
    * `mvn --help`
* ⚠️any time that you specify a phase → ALL the ordered PREVIOUS phases are run ⚠️
  * Check [here](https://www.geeksforgeeks.org/maven-build-phases-and-basic-maven-commands/)
* ⚠️If you have got a project with subprojects → are build in certain order ⚠️
  * Check '../mutiple modules'
* ⚠️Build phases named with `-` → not usually directly called from CL ⚠️
  * **Reason:** 🧠They are intermediate build phases, producing results not useful outside the build lifecycle 🧠

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

## Notes
* NO related to an existing page
  * TODO: Adjust in case we find it