# dev-setup

Configuration process for a new development environment

- SCM: https://github.com/frkline/dev-setup

## Configure your Environment

Prerequisite: Mac OSX 10.9 (Mavericks)

**Install XCode Command Line Tools**
http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/
```
> xcode-select --install
```

**Install Homebrew**
http://brew.sh/
```
> ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
> brew doctor
```

**Install Ruby 1.9**
http://vialstudios.com/guide-authoring-cookbooks.html
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
> i
> if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
> :wq
```

**Verify**
```
> ruby --version
ruby 1.9.3p547 (2014-05-14 revision 45962) [x86_64-darwin13.2.0]
```

**Install Bundler**
Bundler will provide dependency resolution. See http://bundler.io/.
```
> gem install bundler -v ="1.6.3"
```

**Isolate Bundler Installs from System**
```
> vi ~/.bundle/config
> i
> BUNDLE_PATH: ~/.vendor/bundle
> BUNDLE_DISABLE_SHARED_GEMS: "1"
> :wq
```

**Install Vagrant (1.6.3)**
http://www.vagrantup.com/downloads.html

**Install VirtualBox (4.3.12)**
https://www.virtualbox.org/wiki/Downloads

**Perform Workaround for VBox DHCP**
https://github.com/mitchellh/vagrant/issues/3083
```
VBoxManage dhcpserver remove --netname HostInterfaceNetworking-vboxnet0
```
