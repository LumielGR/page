---
title: Guidelines
layout: wiki_base
weight: -200
---

# How to configure your IDE

Configuring IDE is important to starting contribute. We do like preferred use [IntelliJ IDEA](https://www.jetbrains.com/idea/).
Considering other IDE is possible if:

* Have annotation processor support like plugins, extension etc.
* Supporting Gradle project
* Having installed Git (optional supported as plugin or extension)
* Supporting Java Development Kit 8 and late

## Prepare your IDE
Before start we need a [Java Development Kit 8 (JDK8)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Install it and configure environmental variables: `JAVA_HOME` if not exist, create and adding to `PATH` - `$JAVA_HOME/bin`.

### IntelliJ IDEA
[Jetbrains](https://www.jetbrains.com/) provides a most popular IDE for JVM referenced programming language.
It is a great choice to starting journey with this IDE. That's why we recommending it for people who's like programming in Java.

Before starting configuration this IDE we need [download IDE](https://www.jetbrains.com/idea/download/) and [Lombok plugin](https://plugins.jetbrains.com/plugin/6317-lombok-plugin) (you can install it from the **Settings** menu)

* Import project using link for git project. 
	
	Go to **File** > **New** > **Project from Version Control** > **Git**
	Paste your link in **URL** field and press **Clone** to start cloning repository.

* In *bottom-right corner* will shows pop-out which inform the Gradle project has been founded and ready to link. Click **Import Gradle Project**.

	If you lost this pop-out you can find them in **Event Log** (default: *bottom-right tab*)

* Then will shows a window **Import Module from Gradle**. 
	* Uncheck **Create separate module per source set** - this one makes issue in annotation processing.
	* Select **Use gradle 'wrapper' task configuration** - cause we provide gradle wrapper for this repository. We not recommend using a different gradle version cause about tasks works with bundled wrapper.
	* Set **Gradle JVM** if module couldn't found `JAVA_HOME` variable we should add it manually using three dots (`...`) button.
	* Press **OK** and wait till IDE finished importing dependencies
	
### Eclipse
[Eclipse](https://www.eclipse.org) is another choice for advancements programming and old known IDE before IntelliJ.
Before starting configuration this IDE we need [download IDE](https://www.eclipse.org/downloads/) and install [Lombok](/wiki/miscellaneous/project-lombok/) using installer.

* After [installation Eclipse](https://wiki.eclipse.org/Eclipse/Installation), try install a [Project Lombok](/wiki/miscellaneous/project-lombok/#eclipse).
* Import project using link for git project.
	
	For this step we needed make sure if we have booth extensions required for working of this project.
	- [EGit - Git Integration for Eclipse](https://marketplace.eclipse.org/content/egit-git-integration-eclipse)
	- [Buildship Gradle Integration](https://marketplace.eclipse.org/content/buildship-gradle-integration)
	
	If IDE have it implemented in installation we can proceed to the steps below:
	
	- Go to **File** > **Import**  and  select > **Git** > **Projects from Git**.
	- Press **Next >** and select **Clone URI** with pressing **Next >**.
	- Paste your link in **URI** field and press **Next >**.
	- Select specific branches what you need to work with them and press **Next >**.
	- To start cloning repository specify **Directory**, **Initial branch** (recommending select `dev` branch) and **Remote name**. I think you need change only directory because of rest is find and we will leave this.
	- Final step is select **Import as general project**. If we trying use **Import using the New Project wizard**, Gradle extension will not allow us to import, only creation.
	- That's all of them. Import as new **general** project and press **Finish** to start.
	- On the *right side* ide you will find a distinctive a Gradle elephant logo. Click him to expand **Gradle Task View** tab. You will find this message `There are no Gradl;e projects in the current workspace. Import a Gradle project to see its tasks in the Gradle Task View`. Click to **Import a Gradle Project**
	- Specify a **Project root directory** if this field is empty. Sometimes we need specify a Working sets. Create them one using **New** button, and choose **Resource**. Before finishing and selecting our project we must naming a **Working set name**. Than click **Finish**.
	
### Netbeans
[NetBeans](https://www.eclipse.org) IDE is a free and open source integrated development environment for application development on Windows, Mac, Linux, and Solaris operating systems. The IDE simplifies the development of web, enterprise, desktop, and mobile applications that use the Java and HTML5 platforms. The IDE also offers support for the development of PHP and C/C++ applications. Project is associate by Oracle Corporation.

To get started we need first a [Gradle Support](http://plugins.netbeans.org/plugin/44510/gradle-support) plugin and Downloaded [Project Lombok](https://projectlombok.org/download) jar package.

* Before start install [Gradle Support](http://plugins.netbeans.org/plugin/44510/gradle-support) plugin first.

	You can use in menu **Tools** > **Plugins**. In **Available Plugins** tab type `Gradle Support` in search field. Mark them and click **Install**. Shows Installer window, accept a licensing conditions to continue installations. 

* Now it's time to import our project.

  - Go to **Team** > **Git** > **Clone**
  - Paste your link into **Repository URL** field and press **Next >**. Of course before that you can specified Destination Folder for cloning our project.
  - Choose branches for listening. If you want it. Very important!!! You need listen a `dev` branch because we are pushing there before pushing into `master` branch and create Release.
  - In next step select **Checkout Branch** to `dev`, and click **Finish**
  - After cloned project will show information alert when asking us when we want open this project. We will do pressing **Open Project**

Now IDE will automatically finds a Gradle project and will execute tasks for preparing project to start coding. Everything is on the Gradle Plugin.

# How to contribute to Glitch

Of course you can contribute to our repository in 3 ways:

* [Creating Issue](#issue)
* [Joining to our Discord Server](#discord-server)
* [Create Pull Request](#pull-requests)

## Issue

All your ideas, features, bug reports, etc. must be documented in following comments on [issue](https://github.com/glitchlib/glitch/issues/new) tab.
Questions in issue are not welcome. Use Discord server below to asking developers for your question.

## Discord Server

Your problem is a hardest to reproduce? Having a questions, how to and where? Come, join to our [Discord Server](https://discord.gg/nJJ2fDM)

## Pull Requests

So, you are thinking about sending a pull request? Awesome! But... before starting on your pull request, you should read up on
the [pull request](https://github.com/glitchlib/glitch/compare) comment.

Before starting pull request make sure if:

1. All your code will be subject to the project's licence, in this case [MIT](https://github.com/glitchlib/glitch/blob/master/LICENSE).
2. Your code follows a style requirements mentioned below, and you didn't modified project style (ex. indentation style, bracket style, naming, comments, etc). Rewrites of certain systems are kindly welcome too.
3. _Your pull-request must be created **ONLY** against the `dev` branch!_

#### Style Requirements

* All instanced objects should have **getters** and **setters** (where reasonable)
* All POJO classes must be a Kotlin `data class`
* All object instances, methods and fields must be documented for getting sure what does things are doing.
* All implementation subjects are be optional to documenting. Any classes with `Impl` suffix are be ignorable from compiler.
* Documented notes (backslashes `//` or slashed stars `/* */`) is optional into inside methods for getting sure what does things are doing.
* If some parts of code is unofficial and they are using non-documented part of [Twitch API](https://dev.twitch.tv/docs), you must mark them using `@Unofficial("<link to source>")` annotation adding inside the source.
* Documenting object instances (classes, interfaces, enums) must have a same format below:

```java
/**
 * {Your short description}
 * <p>
 * {Your longest description}
 * @author {Full name or Username} [{Github link or e-mail address}]
 * @version %I%, %G%
 * @since {next minor version (eg. 0.11.0)}
 */
public class Example {}
```