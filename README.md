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
brew install rbenv ruby-build
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
source ~/.bash_profile

rbenv install 1.9.3-p448 && rbenv global 1.9.3-p448
rbenv rehash

- Install Bundler
-----------------
gem install bundler
rbenv rehash

- Install Postgres
------------------
brew install postgresql
initdb /usr/local/var/postgres -E utf8
ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

echo "alias pg='pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log'" >> ~/.bash_profile
source ~/.bash_profile
pg start

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
