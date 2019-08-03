---
layout: post
title: "Locking it Down: Enforcing Code Standards Like an Authoritarian"
date: 2018-07-09 11:49:00 -0400
categories: food
---

# All Hail the Repo

## Style & Smell

## Coverage

```
<!-- Code Coverage -->
<plugin>
  <groupId>org.jacoco</groupId>
  <artifactId>jacoco-maven-plugin</artifactId>
  <version>0.8.5-SNAPSHOT</version>
  <executions>
    <!-- Establishes target/site/ -->
    <execution>
        <id>prepare-agent</id>
        <goals>
            <goal>prepare-agent</goal>
        </goals>
    </execution>

    <!-- Publishes coverage report to target/site/ -->
    <execution>
        <id>report</id>
        <phase>test</phase>
        <goals>
            <goal>report</goal>
        </goals>
    </execution>

    <!--
    Ensures the coverage is of a certain threshold during the verify lifecycle
    https://www.eclemma.org/jacoco/trunk/doc/check-mojo.html
    -->
    <execution>
      <id>check</id>
      <goals>
        <goal>check</goal>
      </goals>
      <configuration>
        <rules>
          <rule>
            <element>PACKAGE</element>
            <includes>
              <include>me.stevebass.rootpackage.**</include>
            </includes>
            <limits>
              <limit>
                <counter>LINE</counter>
                <value>COVEREDRATIO</value>
                <minimum>0.80</minimum>
              </limit>
            </limits>
          </rule>
        </rules>
      </configuration>
    </execution>
  </executions>

  <!-- Global config for all JaCoCo behavior -->
  <configuration>
    <excludes>
      <exclude>**/*MyMainClass.java</exclude>
    </excludes>
  </configuration>
</plugin>
</plugins>
```
