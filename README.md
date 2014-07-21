# dev-setup

Configuration process for a new development environment

- SCM: https://github.com/frkline/dev-setup

## Configure Your Environment

Prerequisite: Mac OSX 10.9 (Mavericks)

**Install XCode Command Line Tools**  
For more information see: http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/
```
> xcode-select --install
```

**Install Homebrew**  
For more information see: http://brew.sh/
```
> ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
> brew doctor
```

**Install Ruby 1.9**  
For more information see: http://vialstudios.com/guide-authoring-cookbooks.html
```
> brew install rbenv
> if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
> brew install ruby-build
> rbenv install 1.9.3-p547
> rbenv global 1.9.3-p547
```

**Add Ruby To bash_profile**
```
> vi ~/.bash_profile
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

**Verify**
```
> ruby --version
ruby 1.9.3p547 (2014-05-14 revision 45962) [x86_64-darwin13.2.0]
```

**Install Bundler**  
Bundler will provide dependency resolution. For more information see: http://bundler.io/.
```
> gem install bundler -v ="1.6.3"
```

**Isolate Bundler Installs from System**
```
> mkdir ~/.bundle
> vi ~/.bundle/config
BUNDLE_PATH: ~/.bundle/bundle
BUNDLE_DISABLE_SHARED_GEMS: "1"
```

**Install Vagrant (1.6.3)**  
http://www.vagrantup.com/downloads.html
```
> vagrant plugin install vagrant-berkshelf
> vagrant plugin install vagrant-omnibus
```

**Install VirtualBox (4.3.12)**  
https://www.virtualbox.org/wiki/Downloads

**Perform Workaround for VBox DHCP**  
For more information, see: https://github.com/mitchellh/vagrant/issues/3083
```
> VBoxManage dhcpserver remove --netname HostInterfaceNetworking-vboxnet0
```

## Configure Development Tools

**Install Java 8 JDK**  
Select Mac OS X x64 from the [Java JDK 8 Download Site](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

**Add JAVA_HOME Environment Variable**  
```
> vi ~/.bash_profile
export JAVA_HOME=$(/usr/libexec/java_home)
```

**Install Apache Maven**  
Select version 3.2.2 from the [Apache Maven Download Site](http://maven.apache.org/download.cgi) and move the resulting apache-maven-3.2.2 to ~/tools

**Add M2_HOME to Environment and Maven to PATH**  
```
> vi ~/.bash_profile
export M2_HOME=~/tools/apache-maven-3.2.2
PATH=$M2_HOME/bin:$PATH
```

**Test Maven Installation**
The following should print both the Maven version along with the 1.7 Java version
```
> mvn -version
```

**Create SSH Key for Git**
```
> ssh-keygen -t rsa -C "your_email@example.com"
> pbcopy < ~/.ssh/id_rsa.pub
```

## Configure IntelliJ
We use IntelliJ given its support for deploying into pre-configured environments and functionality across frontend and backend toolchains.

**Install IntelliJ**  
Download IntelliJ IDEA 13 Ultimate Edition from the [IntelliJ Download Site](http://www.jetbrains.com/idea/download/). After installing and starting, select the option for a 30 day trial.

**Configure First-Run Toolsets**  
1. VCS: Disable All > Select (Git)  
2. Web/JavaEE Plugins: Disable All > Select (Application Servers View, Java EE: RESTful Web Services, SQL)  
3. Application Server Plugins: Disable All > Select (Tomcat and TomEE)  
4. HTML/JavaScript Plugins: Disable all > Select (HTML Tools, JavaScript, JavaScript Intention Power Pack, QuirksMode, Spy-js, W3C)  
5. Other Plugins: Disable all > Select (Byte Code Viewer, Cucumber for Java, Emma, JUnit, Maven, Maven Integration Extension, YAML, REST Client, Terminal)  

**Configure Maven**  
1. Select "Configure" from the Welcome screen, or enter the IntelliJ preferences. 
2. Select Maven  
3. Check the "Override" box next to maven home, and choose (your home)/tools/apache-maven-3.2.2
