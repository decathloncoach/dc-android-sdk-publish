# Publication Automatization 

## Usage Guide

* `gradlew clean awsDeploy` - Deploy to remote repo. 
* `gradlew awsRemove` - Remove from remote repo
* `gradlew awsPrintCommands` - Get commands to deploy manually

`awsDeploy` based on `build` and `publishToMavenLocal`.
<br>
Do not use these commands manually. Just deploy your SKD by awsDeploy. 

### Advanced configuration

`m2home`=%PATH_TO_M2% 

* use it when your local maven repository has custom location 
* by default script will search `~/.m2` directory
* Example: `m2home=/Users/developer/.m2`

`awsProfile`=%AWS_PROFILE% 

* use it when you have private repository with credentials
* Example: `awsProfile=developerAwsProfile`

## Requirements

- SDK Gradle Wrapper 4.8
- Wup Digital Maven Publish Plugin 3.6.1
- Dokka Plugin 0.9.17
- Android Kotlin Plugin 1.2.+

## Integration with new SDK

* [Kotlin Library Guide](./src/wiki/kotlin.md)
* [Java Library Guide](./src/wiki/java.md)