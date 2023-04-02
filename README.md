## Overview

This repository is a crude way to package the [developer toolkit](https://phinvads.cdc.gov/vads/developersGuide.action) provided by the CDC Public Health Information Network Vocabulary Access and Distribution System.

Essentially, the PHINVAD API is a series of SOAP based APIs for a set of [public health based vocabularies](https://www.cdc.gov/phin/resources/vocabulary/index.html).

## How to Use

The PHIN vocab client is provided by [Github Packages](https://github.com/boris-ning-usds/phinvad-client/packages/1828045).

### Downloading from a Desktop/Laptop

1. Generate a Github [Personal Access Token](https://docs.github.com/en/packages/learn-github-packages/introduction-to-github-packages#authenticating-to-github-packages) with read-only access to packages. Every pull from Github Package's maven repository is authenticated, unlike Maven Central, which allows you to pull anonymously.
2. Use a local [settings.xml](./settings.xml) or modify an internal ~/.m2/settings.xml to include the generated token.

### Downloading from Maven

Include this block in the Maven pom.xml file.

```java
<project>
  <repositories>
      <repository>
          <id>maven central</id>
          <url>https://repo1.maven.org/maven2</url>
      </repository>
      <repository>
          <id>github</id>
          <url>https://maven.pkg.github.com/boris-ning-usds/phinvad-client</url>
      <snapshots>
          <enabled>true</enabled>
      </snapshots>
      </repository>
  </repositories>
  <dependencies>
    <dependency>
      <groupId>gov.cdc.vocab</groupId>
      <artifactId>phinvads-client</artifactId>
      <version>2.1.0</version>
    </dependency>
  </dependencies>
</project>
```

### Downloading from Gradle Build

Include this block in the Gradle build.gradle file:

```java
maven {
   url = uri(findProperty("github_packages_registry_url"))
   credentials {
      username = project.hasProperty("GITHUB_USERNAME") ? project.findProperty("GITHUB_USERNAME") : System.getenv("GITHUB_USERNAME")
      password = project.hasProperty("GITHUB_TOKEN") ? project.findProperty("GITHUB_TOKEN") : System.getenv("GITHUB_TOKEN")
   }
}
```
