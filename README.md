# Publication Automatization 

## Usage Guide

* `gradlew clean awsDeploy` - Deploy to remote repo. 
* `gradlew awsRemove` - Remove from remote repo
* `gradlew awsPrintCommands` - Get commands to deploy manually

`awsDeploy` based on `build` and `publishToMavenLocal`. You don't need to use these commands manually. Just deploy your SKD by one command. That's it!

### Advanced configuration

`m2home=%PATH_TO_M2% //example:  m2home=~/.m2`

m2home is used when your local m2 repository has custom location. 

By default script will search `~/.m2` directory

`awsProfile=%AWS_PROFILE% //example:  awsProfile=myAwsProfile`

awsProfile is used when you have credentials to your private repository. Such profile will be automatically used by the script.

By default no profile will be used. 

## Requirements

- SDK Gradle Wrapper 4.8
- Wup Digital Maven Publish Plugin 3.6.1
- Dokka Plugin 0.9.17
- Android Kotlin Plugin 1.2.+