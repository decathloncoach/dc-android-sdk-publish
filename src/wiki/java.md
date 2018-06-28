## Integration Guide (kotlin)

> Publication script based on Kotlin Dokka plugin. Which is used for javadoc generation. 
>
> Kotlin plugin won't affect your java library. So it's safe to use with java code.

1. Modify root `build.gradle` 

```groovy
buildscript {
    repositories {
        jcenter()
    }

    dependencies {
        //Use you kotlin version. 1.2.+, it doesn't matter
        classpath 'com.android.tools.build:gradle:1.2.31'
    }
}
```

2. Modify library `library/build.gradle`

```groovy
//At the very top 
apply plugin: 'kotlin-android'  //required for dokka javadoc generation. lib still on pure java
```

3. Follow [kotlin integration guide](kotlin.md) instructions