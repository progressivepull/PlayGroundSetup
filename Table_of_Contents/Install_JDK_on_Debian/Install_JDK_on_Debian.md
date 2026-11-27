# How to Install JDK on Debian
These instructions will install the **OpenJDK (Java Development Kit)** on your Debian Linux system.

I recommend installing OpenJDK 21 LTS or OpenJDK 25 LTS. For general Java development, Java 21 is a good compatibility choice.


## Step 1. Update Debian
Open a terminal and run:

```bash
sudo apt update
sudo apt upgrade -y
```

## Step 2. Install OpenJDK
Install Java 21 JDK:

```bash
sudo apt install -y openjdk-21-jdk
```

This installs:
- Java Runtime Environment (JRE)
- Java compiler (javac)
- Java development tools
- Java standard libraries


## Step 3. Verify Java installation

Check the Java version:

```bash
java -version
```

Check the Java compiler:

```bash
javac -version
```

You should see output similar to:

```
openjdk version "21..."
javac 21...
```

## Step 4. Configure JAVA_HOME

Find the Java installation directory:

```bash
readlink -f "$(which java)"
```

Typically, Debian uses:

```
/usr/lib/jvm/java-21-openjdk-amd64
```


Set the JAVA_HOME environment variable:

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
```


Reload your terminal configuration:

```bash
source ~/.bashrc
```


Verify:

```bash
echo $JAVA_HOME
```

## Step 5. Check installed Java versions

```bash
update-alternatives --list java
```

If you have multiple Java versions, select one:

```bash
sudo update-alternatives --config java
```

## Step 6. Create a test Java program
Create a file:

```bash
nano HelloWorld.java
```

Add:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello from Java on Debian!");
    }
}
```

Compile:

```bash
javac HelloWorld.java
```

Run:

```bash
java HelloWorld
```

Expected output:

```
Hello from Java on Debian!
```

# Installation summary

| Component |	Command |
|---------------------|---------------------|
| Install JDK |	sudo apt install openjdk-21-jdk |
| Check Java |	java -version |
| Check compiler |	javac -version |
| Check JAVA_HOME |	echo $JAVA_HOME |
| Find Java |	which java |

Important: If you are using Debian 13 (Trixie), OpenJDK 21 is available in the official Debian repositories. 
Debian Packages+1


Official package information: Debian OpenJDK 21





















# [README](./../../README.md)