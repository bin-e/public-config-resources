# public-config-resources

## Gradle import

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
