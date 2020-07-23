# Installing and using the W3C Validator plugin in VSCode

## 1. Install the W3C Validation
Search for the [W3C Validation extension](https://marketplace.visualstudio.com/items?itemName=Umoxfo.vscode-w3cvalidation) in VSCode Extensions marketplace and install the one created by Umoxfo:

![W3C Validation Extension](https://i.imgur.com/6VTZve5.png)

## 2. Install Java
The plugin runs on Java. It requires Java 8+ in order to work.
By default, Ubuntu 20.04 includes Open JDK 11, so check if you have it already installed.

```shell
$ java -version
openjdk version "11.0.7" 2020-04-14
OpenJDK Runtime Environment (build 11.0.7+10-post-Ubuntu-3ubuntu1)
OpenJDK 64-Bit Server VM (build 11.0.7+10-post-Ubuntu-3ubuntu1, mixed mode, sharing)
```
If you get the above result, [skip to step 3](#3-setting-the--java_home--environment-variable). If Java is not currently installed, you’ll see a message saying *command not found*. 

Update your package list to make the new software available for installation:
```shell
$ sudo apt update
```
Then execute the following command to install the default Java Development Kit (JDK), which will install the JDK from OpenJDK 11:

```shell
sudo apt install default-jdk
```

Now run the `java -version` command again and you should have it installed.

## 3. Setting the  `JAVA_HOME`  Environment Variable
Many programs written using Java use the  `JAVA_HOME`  environment variable to determine the Java installation location.

First, check if you already have the variable set:
```shell
$ echo $JAVA_HOME
# /usr/lib/jvm/java-11-openjdk-amd64/
```
If you get the above output, [skip to step 4](https://github.com/glaubernespoli/FbW39_Lessons/blob/master/W3C%20Validation/README.md#4-using-the-w3c-validation-extension-in-vscode). If you get an empty line, follow this step.

To set this environment variable, first determine where Java is installed. Use the  `update-alternatives`  command:

```shell
$ sudo update-alternatives --config java
```
This command shows each installation of Java along with its installation path:
```shell
Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-amazon-corretto/bin/java    11100002  auto mode
  1            /usr/lib/jvm/java-11-amazon-corretto/bin/java    11100002  manual mode
* 2            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      manual mode
  3            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode
  4            /usr/lib/jvm/java-8-oracle/jre/bin/java          1081      manual mode
  5            /usr/lib/jvm/java-9-oracle/bin/java              1091      manual mode
  6            /usr/lib/jvm/jdk-11.0.1/bin/java                 2         manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```
Copy the path from your preferred installation. Then open `/etc/environment` using `vim` or your favorite text editor:

```shell
$ sudo vim /etc/environment
```
At the end of this file, add the following line, making sure to replace the highlighted path with your own copied path, but **do not** include the `bin/` portion of the path:

```
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
```
Modifying this file will set the  `JAVA_HOME`  path for all users on your system.

Save the file and exit the editor.

Now reload this file to apply the changes to your current session:

```shell
$ source /etc/environment
```
Verify that the environment variable is set:
```shell
$ echo $JAVA_HOME
# /usr/lib/jvm/java-11-openjdk-amd64/
```
And that's it! You now have your `$JAVA_HOME` variable set correctly.

## 4. Using the W3C Validation extension in VSCode

Open your VSCode (or restart it if you already had it opened).

You should now be able to see HTML and CSS errors in your code during compile time:

![Errors](https://i.imgur.com/dJl0cg2.png)

Once you fix them, the error board will be clear.

![Errors fixed](https://i.imgur.com/IaAlzqa.png)
