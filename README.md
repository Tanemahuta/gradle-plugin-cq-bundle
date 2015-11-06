# Purpose #

This contains a number of plugins for making it easier to work with Gradle and Adobe CQ/AEM.

[ ![Download](https://api.bintray.com/packages/twcable/aem/gradle-plugin-cq-bundle/images/download.svg) ](https://bintray.com/twcable/aem/gradle-plugin-cq-bundle/_latestVersion)

# Installation #

```
buildscript {
    repositories {
        maven {
            url "http://dl.bintray.com/twcable/aem"
        }
    }

    dependencies {
        classpath "com.twcable.gradle:gradle-plugin-cq-bundle:<version>"
    }
}
```

Built against **Gradle 2.8**

# Usage #

`apply plugin: 'com.twcable.cq-bundle'`

## Tasks ##

* `uploadBundle` - Uploads the bundle to the CQ server. The task will fail if the bundle fails to start.
* `deleteBundle` - Removes the current bundle from CQ. This task will not fail if the bundle does not exist.
* `refreshAllBundles` - Tells CQ to refresh all the bundles. This gets added to the top-level project
  and generally a good idea to run after any of the other tasks.
* `showBundle` - Shows a JSON representation of the information CQ has about the bundle, including its status,
  what bundles it is using, and what bundles are using it to STDOUT.

## Configuration ###

### Convention: `slingServers` ###

Creates the `slingServers` convention object. See the "CQ Package Plugin" for details.

### Convention: `bundle` ###

By default, the plugin is initialized with the following effective configuration:

    bundle.with {
      name = project.name
      symbolicName = // computed from project.group and project.name
      installPath = project.slingServers.author.installPath
      sourceFile = project.jar.archivePath
      slingServers = project.slingServers
    }

`bundle` also has a `felixId` property that the plugin tries to determine dynamically from the server based on the
bundle's symbolic name.

# API #

https://twcable.github.io/gradle-plugin-cq-bundle/docs/groovydoc/

# LICENSE

Copyright 2015 Time Warner Cable, Inc.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance
with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on
an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for
the specific language governing permissions and limitations under the License.