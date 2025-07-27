# SHAFT_Engine: TestNG Archetype

This is a Maven Archetype for setting up a sample SHAFT_Engine + TestNG project.

To Generate a project just follow these simple steps:

1. [Download the latest version of mvn](https://maven.apache.org/download.cgi)
2. [Add it to your PATH variable](https://maven.apache.org/install.html)
3. Create a new directory for the project, and navigate to it.
4. Open a Terminal window in the target directory and execute the below command.
```shell
mvn archetype:generate "-DarchetypeGroupId=io.github.shafthq" "-DarchetypeArtifactId=testng-archetype" "-DarchetypeVersion=${archetype.version}" "-DinteractiveMode=false" "-DgroupId=io.github.shafthq" "-DartifactId=using_SHAFT_Engine"
```
**_NOTE 1: Replace `${archetype.version}` with [the latest SHAFT_Engine: TestNG Archetype version](https://github.com/ShaftHQ/testng-archetype/releases/latest)._**
<br/>**_NOTE 2: Customize `"-DgroupId=io.github.shafthq"` and `"-DartifactId=using_SHAFT_Engine"` with the groupId and artifactId that you want to use for the new project._** 
