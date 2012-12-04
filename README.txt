Hadoop Maven plugins

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
Available goals:

  * version-info
  * protoc

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

Goal details:

--------------------------------------------------------------------------------
* version-info, by default runs in the 'initialize' phase

Calculates and injects as POM properties version information
(source MD5, SCM URI, SCM branch, SCM commit).

The properties can be used by Other Maven plugins and for Maven
driven token replacement in properties files.

Configuration:

<plugin>
  <groupId>org.apache.hadoop.maven.plugin</groupId>
  <artifactId>hadoop-maven-plugins</artifactId>
  <executions>
    <execution>
      <id>version-info</id>
      <goals>
        <goal>version-info</goal>
      </goals>
      <configuration>

        <source>
          <directory>${basedir}/src/main/java</directory>
          <includes>
            <include>**/*.java</include>
          </includes>
        </source>

        <!-- Optional configuration, shown with default values -->
        <buildTimeProperty>version-info.build.time</buildTimeProperty>
        <md5Property>version-info.source.md5</md5Property>
        <scmUriProperty>version-info.scm.uri</scmUriProperty>
        <scmBranchProperty>version-info.scm.branch</scmBranchProperty>
        <scmCommitProperty>version-info.scm.commit</scmCommitProperty>
        <gitCommand>git</gitCommand>
        <svnCommand>svn</svnCommand>

      </configuration>
    </execution>
  </executions>
</plugin>

--------------------------------------------------------------------------------
* protoc,  by default runs in the 'generate-sources' phase

Compiles protobuffer .proto files to Java sources and adds the output directory
to Maven's compile sources directory

<plugin>
  <groupId>org.apache.hadoop.maven.plugin</groupId>
  <artifactId>hadoop-maven-plugins</artifactId>
  <executions>
    <execution>
      <id>compile-protoc</id>
      <goals>
        <goal>protoc</goal>
      </goals>
      <configuration>
        <source>
          <directory>${basedir}/src/main/proto</directory>
          <includes>
            <include>*.proto</include>
          </includes>
        </source>

        <!-- Optional configuration, shown with default values -->
        <imports>
          <param><!-- no default --></param>
          ...
        </imports>
        <output>${project.build.directory}/generated-sources/java</output>
      </configuration>
    </execution>
  </executions>
</plugin>

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
