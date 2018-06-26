# Publication Automatization 

## Requirements

- SDK Gradle Wrapper 4.8
- Wup Digital Maven Publish Plugin 3.6.1
- Dokka Plugin 0.9.17

## Steps to add

1. Update your `/gradle/wrapper/gradle-wrapper.properties`:

```text
distributionUrl=https\://services.gradle.org/distributions/gradle-4.8-all.zip
```

2. Add to `/build.gradle` 

```groovy
buildscript {
    apply from: "gradle/version.gradle"
    //...
    dependencies {
        //...
        classpath plugin.maven_publish
        classpath plugin.dokka
    }
}
```

3. Create `/gradle/version.gradle` file with your project params

```groovy
ext.config = [
        build: [
                code: 'VERSION_CODE',
                name: 'VERSION_NAME',
                groupId: 'PACKAGE',
                artifactId: 'LIBRARY'
        ]
]

ext.versions = [
        maven_publish: "3.6.1",
        dokka: "0.9.17",
]

ext.plugin = [
        maven_publish: "digital.wup:android-maven-publish:$versions.maven_publish",
        dokka: "org.jetbrains.dokka:dokka-gradle-plugin:$versions.dokka"
]
```

4. Add to your module `/library/build.gradle`

```groovy
apply from: 'https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/publication.gradle'
```

## How to use

1. run `gradlew clean build publishToMavenLocal`
2. go to `~/.m2` and publish artifacts to server
