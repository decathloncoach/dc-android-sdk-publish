# Publication Automatization 

1. Add to your root `/build.gradle`

```groovy
ext.config = [
        build: [
                code: 'VERSION_CODE',
                name: 'VERSION_NAME',
                groupId: 'PACKAGE',
                artifactId: 'LIBRARY'
        ]
]
```

2. Add to your module `/library/build.gradle`

```groovy
apply from: 'https://raw.githubusercontent.com/decathloncoach/dc-android-sdk-publish/master/publication.gradle'
```

