# Publication Automatization 

## Requirements

- SDK Gradle Wrapper 4.8
- Wup Digital Maven Publish Plugin 3.6.1
- Dokka Plugin 0.9.17

**Gradle Wrapper 4.4+ has deprecated configure on demand feature**

- issue: https://github.com/gradle/gradle/issues/2868
- disable in studio: https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/configure-on-demand.png

## Steps to add

1. Update your `/gradle/wrapper/gradle-wrapper.properties`

```text
distributionUrl=https\://services.gradle.org/distributions/gradle-4.8-all.zip
```

2. Add to root `/build.gradle` 

```groovy
buildscript {
    apply from: 'gradle/version.gradle' //publish constants
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'digital.wup:android-maven-publish:3.6.1'
        classpath 'org.jetbrains.dokka:dokka-gradle-plugin:0.9.17'
    }
}
```

3. Create `/gradle/version.gradle` file with your project params

```groovy
ext.config = [
        build: [
                code: 'VERSION_CODE', // int
                name: 'VERSION_NAME', // string
                groupId: 'PACKAGE',   // string
                artifactId: 'LIBRARY' // string
        ]
]
```

4. Add to your module `/library/build.gradle`

```groovy
apply from: 'https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/publication.gradle'
```

## How to use

### Preconfiguration

Add to project `local.properties` 

* m2home=%PATH_TO_M2% `//example:  m2home=~/.m2`
* awsProfile=%AWS_PROFILE% `//example:  awsProfile=myAwsProfile`

It could be empty or missing - then default values will be used.

### Deploy 

`gradlew clean awsDeploy`

### Remove from remote repo

`gradlew awsRemove`

### Get commands to deploy manually

`gradlew awsPrintCommands`
