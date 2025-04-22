* TODO:

# Project Interpolation and Variables
* `${someVariableToEvaluate}`
  * restrictions
    * 👁️ once inherit -> it's evaluated 👁️
      * TODO: Check after comprehend inheritance
## Available variables
* project model variables
  * `${project.anyFieldWhichIsASingleValueElement}` / `${pom.anyFieldWhichIsASingleValueElement}` 
    * 👁`project` or `pom` refer both to the same == current pom.xml 👁
    * Check '../pomReference' to check available `anyFieldWhichIsASingleValueElement`
* special built-in variables
  * `project.basedir`
    * == directory / pom.xml resides in
  * `project.baseUri`
    * == `project.basedir` / -- represented as -- URI
  * `maven.build.timestamp`
    * := timestamp (UTC) / build start
    * `maven.build.timestamp.format`
      * allows
        * customizing the format -- via -- [SimpleDateFormat](https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html) --
* any variable defined under `<properties></properties>`


# Examples
* TODO:
* Project Interpolation and Variables
  * Check 'InterpolationAndVariables/'
