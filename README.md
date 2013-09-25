Setting Up a Dev Environment for Ruby on Rails on Mac OSx
=============================

Preparing for Ruby
------------------
- Get a Github account
----------------------
http://www.github.com

- Install XCode
---------------
https://developer.apple.com/xcode/

- Install Command Line Tools for Xcode
--------------------------------------

- Install Homebrew
------------------
http://brew.sh/

ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"

brew update

- Install Git
-------------
brew install git

- Install Rbenv and Ruby-build
------------------------------

```bash
brew install rbenv ruby-build
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
source ~/.bash_profile

rbenv install 1.9.3-p448 && rbenv global 1.9.3-p448
rbenv rehash
```
- Install Bundler
-----------------

```bash
gem install bundler
rbenv rehash
```

- Install Postgres
------------------

```bash
brew install postgresql
initdb /usr/local/var/postgres -E utf8
ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

echo "alias pg='pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log'" >> ~/.bash_profile
source ~/.bash_profile
pg start
```

- Install a text Editor
-----------------------
- install Sublime Text 2: http://www.sublimetext.com/
- make and install TextMate (I'm not helping you with this...someone else can make the
  tutorial...it was a pain in the ass for me)

- Install SourceTree for graphical Git management
-------------------------------------------------
http://www.sourcetreeapp.com/

- Download/Install the environment
----------------------------------

```ruby
git clone https://github.com/Dominus-Development/site-subdomains.git

cd site-subdomains/www/
gem install bundler
rbenv rehash
bundle install
bundle exec wagon pull production
```

Setting Up a Dev Environment for Ruby on Rails on Linux (Debian based)
=============================

Preparing for Ruby
------------------
- Get a Github account
----------------------
http://www.github.com

Bash Instructions
-----------------
Install Dependencies:
```bash
apt-get update
apt-get install git build-essential zlib1g-dev libreadline-dev libssl-dev libcurl4-openssl-dev libxslt-dev libxml2-dev
```
Install Rbenv and Ruby-build:
```bash
git clone git://github.com/sstephenson/rbenv.git ~/.rbenv
git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc

rbenv install 1.9.3-p448 && rbenv global 1.9.3-p448
rbenv rehash
```
Clone Site Repo:
```bash
git clone https://github.com/Dominus-Development/site-subdomains.git

cd site-subdomains/www/
gem install bundler
rbenv rehash
bundle install
bundle exec wagon pull production
```

- Install a text Editor
-----------------------
- install Sublime Text 2: http://www.sublimetext.com/
- make and install TextMate (I'm not helping you with this...someone else can make the
  tutorial...it was a pain in the ass for me)

Setting Up a Dev Environment for Ruby on Rails on Windows XP SP2
=============================

Preparing for Ruby
------------------
- Get a Github account
----------------------
http://www.github.com

- Install MySysGit
---------------
http://msysgit.github.io/
I recommend the latest Full Installer
- Run the installer
- Install to your preferred location on the disk
- Choose some of the integration tools if you want to use Windows Explorer to do file system navigation
- 'Adjusting your PATH environment' Screen - Choose 'Run Git from the Windows Command Prompt'
- 'Configuring the line ending conversions' Screen = Choose 'Checkout Windows-style, commit Unix-style line endings'
- Finish the installation

- Install Ruby
------------------------------
Use RubyInstaller's Windows Ruby installer:
http://rubyinstaller.org/downloads/

Choose the appropriate Ruby version for your environment. For now, choose Ruby 1.9.3-p448
Run the installer
- I recommend installing to C:/Ruby193
- Make sure to select 'Add Ruby executables to your PATH'
- Finish installation

- Install Pik
-------------------------------
- Open a Command Prompt window with Administrator permissions

```bash
>gem install pik
```

- Install pik to a location that is already in your path. For example, my path looks like so:

```bash
>path
PATH=C:\Ruby193\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\Program Files\Git\cmd
```

So I install pik to C:\WINDOWS (I could, alternately, add another location to my path,but that is
beyond the scope of this tutorial)

```bash
>pik_install C:\WINDOWS
```

- Install Devkit
-----------------
This page provides a fantastic guide if you run into problems:
https://github.com/oneclick/rubyinstaller/wiki/Development-Kit

Make sure to install the correct DevKit for your Ruby version (we're using 1.9.3) and machine (32bit/64bit):
http://rubyinstaller.org/downloads/

For 1.9.3, you are going to want DevKit-tdm-32

- Run the installer
- Extract to a directory WITHOUT SPACES IN THE NAME. C:\DevKit is the standard.
  Do NOT change this directory name down the road. This directory will be hereafter referred to as %devkit%
- Open a command prompt and cd to %devkit%
- run the following command

```bash
>ruby dk.rb init
```
- there will now be a config.yml file in the %devkit% directory
- open it with any text editor. The file should match the following (disregarding comments):

```yaml
---
- C:/Ruby193
```
- Now run the command:

```bash
>ruby dk.rb install
```

- Confirm that everything is running by running the following:

```bash
>gem install json --platform=ruby
```
- You should see the gem install successfully and see "with native extensions" in some of the screen messages
- You can test that the following gives you the correct output:

```bash
>ruby -rubygems -e "require 'json'; puts JSON.load('[42]').inspect"
[42]
```

- Install Bundler
-----------------

```bash
gem install bundler
```

- Install a text Editor
-----------------------
- install Sublime Text 2: http://www.sublimetext.com/

- Install SourceTree for graphical Git management
-------------------------------------------------
http://www.sourcetreeapp.com/

- Download/Install the environment
----------------------------------
- Run the following commands in your project directory:

```ruby
git clone https://github.com/Dominus-Development/site-subdomains.git

cd site-subdomains/www/
bundle install
bundle exec wagon pull production
```

