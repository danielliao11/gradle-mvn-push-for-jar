#gradle_mvn_push_for_jar
I used [Chris Banes](https://plus.google.com/+ChrisBanes/posts?partnerid=ogpy0)'s [gradle-mvn-push](https://github.com/chrisbanes/gradle-mvn-push) and modify it for jar to my [gradle_mvn_push_for_jar](https://github.com/saintdan/gradle_mvn_push_for_jar). 
THX Chris!  

Maybe you need a complete guide of [Upload your jar to Maven Central with Gradle](http://saintdan.github.io/2015/04/16/Publish-your-jar-file-to-Maven-Central-with-Gradle/).  

##Usage

###1.Download files to your project root
Download the **'build.gradle'** and **'gradle.properties'** to your project root.
###2.If you have no sub-projects
Just keep downloaded files in your project root.
###3.If you have some sub-projects
Create **'gradle.properties'** in each sub-project and copy following in them:

```
POM_NAME = <your project name>
POM_ARTIFACT_ID = <your artifact id>
POM_PACKAGING = jar
```

Add the following at the end of each sub-modules build.gradle that you wish to upload:

```
apply from 'gradle_mvn_push_for_jar.gradle'
```

or

```
apply from 'https://github.com/saintdan/gradle_mvn_push_for_jar/master/gradle_mvn_push_for_jar.gradle'
```
###4.Update your home gradle.properties
This will include the username and password to upload to the Maven server.

And may also include your signing key id, password, and secret key ring file (for signed uploads). Signing is only necessary if you're putting release builds of your project on maven central.

So that they are kept local on your machine for security.

The location defaults to **USER_HOME/.gradle/gradle.properties**.

###5.Build and Push
You can build and push with:

```
$ gradle clean build uploadArchives
```


