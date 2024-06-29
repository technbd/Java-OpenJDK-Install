

## Installing Java on CentOS-7: 

There are three different editions of the Java Platform: **Standard Edition (SE)**, **Enterprise Edition (EE)**, and **Micro Edition (ME)**. This tutorial is focused on Java SE (Java Platform, Standard Edition). Almost all open source Java software is designed to run with Java SE.

There are two different Java SE packages that can be installed: the **Java Runtime Environment (JRE)** and the **Java Development Kit (JDK)**. JRE is an implementation of the Java Virtual Machine (JVM), which allows you to run compiled Java applications and applets. The JDK includes the JRE as well as other software that is required for writing, developing, and compiling Java applications and applets.

There are also two different implementations of Java, **OpenJDK** and **Oracle Java**, with almost no differences between them except that Oracle Java has a few additional commercial features.



```
yum update
```



```
rpm -qa | grep java
rpm -qa | grep jdk
```


```
yum list installed | grep java

or,

yum list --installed | grep java
```


## Install OpenJDK-8:
Install the OpenJDK 8 package using the following command:

```
### Install OpenJDK 8 JRE:

yum install java

or,

yum install java-1.8.0-openjdk
```


```
### Install OpenJDK 8 JDK:


yum install java-devel

or,

yum install java-1.8.0-openjdk-devel
```


```
java -version

openjdk version "1.8.0_412"
OpenJDK Runtime Environment (build 1.8.0_412-b08)
OpenJDK 64-Bit Server VM (build 25.412-b08, mixed mode)
```


### Set JAVA HOME:

```
which java

  /usr/bin/java
```


```
readlink -f $(which java)

or,

readlink -f /usr/bin/java

  /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.412.b08-1.el7_9.x86_64/jre/bin/java
```


```
vim /etc/profile.d/java-8.sh

export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.412.b08-1.el7_9.x86_64/jre
#export JRE_HOME=
export PATH=$PATH:$JAVA_HOME/bin
```


```
source /etc/profile.d/java-8.sh
```



### Remove OpenJDK-8:

```
yum remove java-1.8.0*

or,

yum remove java-1.8.0-openjdk
yum remove java-1.8.0-openjdk-devel
```



---
---



## Install OpenJDK-11:
Install the OpenJDK 11 package using the following command:

```
### Install OpenJDK 11 JRE:

yum install java-11-openjdk -y
```



```
### Install OpenJDK 11 JDK: 

yum install java-11-openjdk-devel -y
```


```
java --version
java -version


openjdk version "11.0.23" 2024-04-16 LTS
OpenJDK Runtime Environment (Red_Hat-11.0.23.0.9-2.el7_9) (build 11.0.23+9-LTS)
OpenJDK 64-Bit Server VM (Red_Hat-11.0.23.0.9-2.el7_9) (build 11.0.23+9-LTS, mixed mode, sharing)
```



### Set JAVA HOME:

```
which java

  /usr/bin/java
```


```
readlink -f /usr/bin/java

  /usr/lib/jvm/java-11-openjdk-11.0.23.0.9-2.el7_9.x86_64/bin/java
```



```
vim /etc/profile.d/java-11.sh

export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.23.0.9-2.el7_9.x86_64
#export JRE_HOME=
export PATH=$PATH:$JAVA_HOME/bin
```


```
source /etc/profile.d/java-11.sh
``` 



### Remove OpenJDK-11:  

```
yum remove java-11* -y

or,

yum remove java-11-openjdk* -y
yum remove java-11-openjdk-devel -y
```




---
---




## Install OpenJDK-17:
Install the OpenJDK 17 package using the following command:

```
yum install java-17-openjdk -y
yum install java-17-openjdk-devel -y
```


or,


```
wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.rpm
```


_Use 'yum' or 'rpm' commands to install the package:_

```
rpm -ivh jdk-17_linux-x64_bin.rpm

or,

yum install jdk-17_linux-x64_bin.rpm

or,

yum localinstall jdk-17_linux-x64_bin.rpm

```


```
java -version


java version "17.0.11" 2024-04-16 LTS
Java(TM) SE Runtime Environment (build 17.0.11+7-LTS-207)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.11+7-LTS-207, mixed mode, sharing)
```



### Set JAVA HOME:

```
which java

  /usr/bin/java
```


```
readlink -f /usr/bin/java
```



```

```



### Remove OpenJDK-17:  

```
rpm -qa | grep jdk

jdk-17-17.0.11-7.x86_64
```


```
rpm -e jdk-17-17.0.11-7.x86_64

or,

yum remove jdk-17-17.0.11-7.x86_64
```




### Set the Default Java Version:

This `alternatives --config java` command will display a list of installed versions of Java, and you will be prompted to select the version you want to use as the default.

```
update-alternatives --display java
```



```
update-alternatives --config java

There are 2 programs which provide 'java'.

  Selection    Command
-----------------------------------------------
*+ 1           java-1.8.0-openjdk.x86_64 (/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.412.b08-1.el7_9.x86_64/jre/bin/java)
   2           java-11-openjdk.x86_64 (/usr/lib/jvm/java-11-openjdk-11.0.23.0.9-2.el7_9.x86_64/bin/java)

Enter to keep the current selection[+], or type selection number:
```


or,


```
alternatives --config java

There are 2 programs which provide 'java'.

  Selection    Command
-----------------------------------------------
*+ 1           java-1.8.0-openjdk.x86_64 (/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.412.b08-1.el7_9.x86_64/jre/bin/java)
   2           java-11-openjdk.x86_64 (/usr/lib/jvm/java-11-openjdk-11.0.23.0.9-2.el7_9.x86_64/bin/java)

Enter to keep the current selection[+], or type selection number:
```


```
java -version
```


By following these steps, you can install Java (OpenJDK) on CentOS 7 and optionally set the JAVA_HOME environment variable to ensure Java is properly configured on your system. Adjust the version numbers and paths according to your specific requirements.


---
---





## Installing Java on Ubuntu: 
To install Java on an Ubuntu system, you can follow these steps. Ubuntu uses the `apt` package manager to install software.


```
dpkg -l | grep openjdk-8
dpkg -l | grep openjdk-11
```


```
apt list --installed | grep openjdk-8
apt list --installed | grep openjdk-11
```


## Install OpenJDK-8:
The JDK (`openjdk-<version>-jdk`) package includes everything you need for Java development, including the compiler (javac), runtime (java), and various tools (jar, javadoc, etc.).


```
apt update

apt install -y openjdk-8-jdk

or,

apt install -y openjdk-8-jre
```


```
java -version

openjdk version "1.8.0_412"
OpenJDK Runtime Environment (build 1.8.0_412-8u412-ga-1~20.04.1-b08)
OpenJDK 64-Bit Server VM (build 25.412-b08, mixed mode)
```


### Remove OpenJDK-8:

```
apt remove --purge openjdk-8* -y

apt autoremove -y
```


---
---



## Install OpenJDK-11:

```
apt install -y openjdk-11-jdk

or,

apt install -y openjdk-11-jre
```


```
java -version

openjdk version "11.0.23" 2024-04-16
OpenJDK Runtime Environment (build 11.0.23+9-post-Ubuntu-1ubuntu120.04.2)
OpenJDK 64-Bit Server VM (build 11.0.23+9-post-Ubuntu-1ubuntu120.04.2, mixed mode, sharing)
```



### Remove OpenJDK-11:

```
apt remove --purge openjdk-11* -y
```



### Set the Default Java Version:


```
which java

    /usr/bin/java
```


```
readlink -f $(which java)

or,

readlink -f /usr/bin/java

    /usr/lib/jvm/java-11-openjdk-amd64/bin/java
```


```
update-alternatives --config java


There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java      1111      manual mode
  2            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode

Press <enter> to keep the current choice[*], or type selection number: 
```



```
java -version
```



### Links:
- [Java-17](https://www.oracle.com/java/technologies/downloads/#java17)



By following these steps, you can install the OpenJDK development kit (JDK) on your Ubuntu system and verify its installation. This setup allows you to develop and run Java applications locally.


