### Java environment viriable
// Java version 1.8.0.211
JAVA_HOME_8=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
// Java version 18.0.2.1
JAVA_HOME_18=/Library/Java/JavaVirtualMachines/jdk-18.0.2.1.jdk/Contents/Home

PATH=$JAVA_HOME/bin:$PATH:.

export JAVA_HOME=$JAVA_HOME_18

alias jdk8="export JAVA_HOME=$JAVA_HOME_8"
alias jdk18="export JAVA_HOME=$JAVA_HOME_18"

export PATH

### 切换Java版本
open ~/.zshrc
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home
// Java 18.0.2.1 version
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-18.0.2.1.jdk/Contents/Home
CLASS_PATH="$JAVA_HOME/lib"
PATH=":$PATH:$JAVA_HOME/bin"

### Tomcat
sudo startup.sh
shutdown.sh
