Setup environment
=================

Introduction
------------

Environement setup is something that if you don't do right the first time around
it will come back to haunt you because you will spend a lot of time fighting
with your tools instead of your tools helping you.  Also, installing tools with
`sudo` can result in you having to use that tool with `sudo` for every command.
When downloading things like node modules off the internet this could be a very
bad idea.  So don't use `sudo` unless it is specifically listed used below.

User setup
----------
- Create a new user named `developer` as an administrator, when install is
complete you can optionally remove administrator access
- Do any icloud, email, calendar, or contacts setup as necessary

Manual Download Applications
----------------------------
- Slack (App store)
- Komodo Edit (http://komodoide.com/download/edit-osx/#)
- Sublime (@todo)
- Install SourceTree (https://www.sourcetreeapp.com/download/)
- iTerm (https://iterm2.com/downloads/stable/iTerm2-2_1_4.zip)

Pre Install Configuration
-------------------------
- Setup SSH Key
- Setup SSH Key on GitHub
- Setup SSH Key on Pantheon
- Setup SSH Key on Acquia
- Run pre-install.sh to setup home_directory files

Turn on FileVault
--------------------
- Open system preferences
- Go to security
- Go to FileVault
- Turn it on
- Enable boot login accounts
- Restart your computer
- Continue the install process while this runs in the background

Setup Time Machine
------------------
- If you have an external drive, network drive, or Apple server hosting time
machine.  Go ahead and set this up now.
- Optionally, if you wait for FileVault and Time Machine to complete you will
have a fresh install avaliabe at this point to restore to if needed.

Carbon Copy Clone
-----------------
- Optionally, setup a carbon copy clone at this point so you will have a fresh
install to restore to.

Install Tools
=============

Setup homebrew
--------------
Installation.md: [https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Installation.md](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Installation.md)

### Install homebrew:
- `sudo chown developer:wheel /usr/local`
- `cd /usr/local`
- `mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew`
- `export PATH=$PATH:/usr/local/homebrew/bin`

### Install git:
- `brew update`
- `brew install git` (git)

### Install php:
- `brew tap homebrew/dupes`
- `brew tap homebrew/versions`
- `brew tap homebrew/php`
- `brew install PHP56 --with-pear`

### Install composer:
- `brew install composer`

### Install zsh:
- `brew install zsh` (this should be last to prevent weird errors)

### Install DrupalVM related tools:
- `brew cask install virtualbox`
- `brew cask install vagrant`
- `brew install ansible`

Installing drush
----------------
[http://docs.drush.org/en/master/install/](http://docs.drush.org/en/master/install/)
[https://github.com/drush-ops/drush](https://github.com/drush-ops/drush)
[https://www.lullabot.com/articles/switching-drush-versions](https://www.lullabot.com/articles/switching-drush-versions)

### Install drush 8.x:
- `mkdir ~/drush8`
- `cd ~/drush8`
- `composer require "drush/drush:8.*"`

### Install drush 7.x:
- `mkdir ~/drush7`
- `cd ~/drush7`
- `composer require "drush/drush:7.*"`

### Create aliases:
- `alias drush7='~/drush7/vendor/bin/drush'`
- `alias drush8='~/drush8/vendor/bin/drush'`

### Test:
- `drush7 --version`
- `drush8 --version`

Setup Git
---------
This is how your commits will be stored.
- git config --global user.email "name@example.com"
- git config --global user.name "Firstname Lastname"

File Structure
--------------
- `mkdir ~/repos` (git clone here)
- `mkdir ~/vms` (Vagrantfile here)
- `mkdir ~/patches` (contrib patches here)
- `mkdir ~/sql` (.sql files here - exclude from backups)
- `mkdir ~/VirtualBox\ VMs` (Virtual Machines Here - exclude from backups)

Virtual Machines
================

DrupalVM
--------
- `cd ~/vms/`
- `git clone git@github.com:geerlingguy/drupal-vm.git`
- For existing machines get the exiting config.yml and drop it into the new
directory.
- For new machines copy the example.config.yml to config.yml and configure.

Hosts
=====

Setup terminus for Pantheon
---------------------------
- `composer require pantheon-systems/terminus`
- Log in and setup machine tokens

Code Linting
============

Setup phpcs
-----------
- `pear install PHP_CodeSniffer` (it might be possible this isn't needed)
- `composer global require drupal/coder`
- `phpcs --config-set installed_paths ~/.composer/vendor/drupal/coder/coder_sniffer`

JS linting
----------
- eslint (http://eslint.org/docs/user-guide/getting-started)
- `npm install -g eslint`

RVM
====

Setup RVM
---------
- @todo

Setup bundler
-------------
- `gem install bundler`

Node
====

NVM
----
- `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash`
- `npm install gulp -g`
- `npm install grunt -g`

SQL
====

Setup SequelPro
---------------
- Get your favorites from ~/Library/Application\ Support/SequelPro/Data/Favories.xml
- @TODO Verify Above Path and add download link


Post Install Process
====================

Security
--------
- Optionally, remove administrator access (this is for people very concerned
about security)

Carbon Copy Clone
-----------------
- Optionally, run carbon copy clone at this point so you will have a fresh
install to restore to.


Author's Picks
==============

Install Menu Meters
-------------------
- http://member.ipmu.jp/yuji.tachikawa/MenuMetersElCapitan/

SMC Fan Control
---------------
- You only have to have one mac melt on you before you install this on every
computer.
- http://www.macupdate.com/app/mac/23049/smcfancontrol/download

Postman
-------
- Download chrome app

Markdown Viewing
----------------
- `brew cask install macdown`

Other
----------------------------
- Drag your /Applications/Utilities folder to the dock (on the side near the
trash)