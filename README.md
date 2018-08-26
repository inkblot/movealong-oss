# movealong-oss
Parent POM for OSS maven projects

This POM is intended to be used as the parent my other open source projects. It declares the maven `license` and `developers` metadata, and so it probably isn't suitable for your project except as an example.

To use it anyway, you could clone this repo next to your project and add this to your POM:

```
<parent>
  <groupId>org.movealong</groupId>
  <artifactId>movealong-oss</artifactId>
  <version>1.0-SNAPSHOT</version>
  <relativePath>../movealong-oss</relativePath>
</parent>
```

The POM provides some plugin configurations, plugin management, and depedency management in addition to supplying stock metadata. These are intended to make a project OSSRH conformant with minimal boilerplate:

```
<build>
  <plugins>
    <plugin>
      <groupId>org.codehaus.mojo</groupId>
      <artifactId>flatten-maven-plugin</artifactId>
    </plugin>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-gpg-plugin</artifactId>
    </plugin>
  <plugins>
</build>
```
