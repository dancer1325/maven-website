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

## Notes
* NO related to an existing page
  * TODO: Adjust in case we find it