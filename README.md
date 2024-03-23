# public-config-resources

## gradle import (public-resources) 

``` gradle 
https://raw.githubusercontent.com/jeongph/public-resources/gradle/{gradle_version}/spring-boot/{spring_version}/{file_name}
```

``` gradle 
// e.g. 
https://raw.githubusercontent.com/jeongph/public-resources/gradle/8.6/spring-boot/3.2.4/querydsl.gradle
```


## build.gardle

``` gradle
buildscript {
    ext { // BOM 
        springBootVersion = '3.2.4'
        springCloudVersion = '2023.0.0'
    }

    repositories {
//        mavenLocal()
//        maven {
//            url "${mavenReleasesRepositoryUrl}"
//            credentials {
//                username System.getenv("MAVEN_USERNAME")
//                password System.getenv("MAVEN_PASSWORD")
//            }
//        }
        mavenCentral()
    }

    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:$springBootVersion")
    }
}

subprojects {
    apply plugin: 'java'
    apply plugin: 'idea'
    apply plugin: 'org.springframework.boot'
    apply plugin: 'io.spring.dependency-management'

    group = 'me.jeonguk'
    version = '0.0.1-SNAPSHOT'

    bootJar.enabled false
    jar.enabled true

    java {
        sourceCompatibility = '17'
    }

    configurations {
        compileOnly {
            extendsFrom annotationProcessor
        }
    }

    repositories {
        mavenCentral()
    }

    dependencies {
        testImplementation 'org.junit.jupiter:junit-jupiter:5.7.1'
        testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
    }

    tasks.named('test') {
        useJUnitPlatform()
    }
}
```
