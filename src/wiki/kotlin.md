## Integration Guide (kotlin)

1. Update Gradle Wrapper `/gradle/wrapper/gradle-wrapper.properties`

```text
distributionUrl=https\://services.gradle.org/distributions/gradle-4.8-all.zip
```

**Note**: Gradle Wrapper 4.4+ has deprecated configure on demand feature

- [github gradle issue](https://github.com/gradle/gradle/issues/2868)
- [how to disable in studio?](https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/src/img/configure-on-demand.png)

2. Create `/gradle/version.gradle` file with your project params

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

It's important to keep such constants together. 

They will be used for publishing script and for android library configuration.

3. Modify root `/build.gradle` 

```groovy
buildscript {
    apply from: 'gradle/version.gradle' 
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'digital.wup:android-maven-publish:3.6.1'
        classpath 'org.jetbrains.dokka:dokka-gradle-plugin:0.9.17'
    }
}
```

apply from `version.gradle` makes ext visible for your modules. 

Gradle does not support buildscript modification from external files, you have to add plugin classpath manually.

4. Add to your module `/library/build.gradle`

```groovy
apply from: 'https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/publication.gradle'
```

Finally add script to your library module. That will add tasks for publication. 