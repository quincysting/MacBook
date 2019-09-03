# MacBook Setup Guide

This is a detailed step-by-step guide to help you setup a new MacBook Pro. Before we start, please take note of the following items:

- It is assumed you are using the latest model of MacBook Pro (at least after 2016).
- It is also assumed that you have installed the latest version of MacOS (at least `10.12 Sierra`).
- This guide is tailor-made for a developer or software engineer's personal laptop.
    - In other words, we would install the required tools for personal development. However, we would not focus on tools that are organization-specific.
- This guide is also customized for certain region (Asia/Singapore) & languages (English and Mandarin).

## Background

At the time of writing, I am a [Computer Engineering](http://ceg.nus.edu.sg) undergraduate at the [National University of Singapore](http://www.nus.edu.sg/) as well as a software development enthusiast.

One day, I received an email from [Apple](https://www.apple.com) with the title _"Important information about your MacBook Pro"_. It said that my MacBook _has an issue that may result in data loss and failure of the drive (SSD)._ See [this page](https://www.apple.com/sg/support/13-inch-macbook-pro-solid-state-drive-service-program/) for more information. Apple offered to provide a service program to fix this problem _(by updating the driver firmware)_ free of charge. So I registered and sent the device to an Apple Authorized Service Provider - [A.Lab](https://www.alab.sg).

I am aware that all data will be erased after the service. However, I am fine with that since almost all important data on my device have been backed up. Nonetheless, I still need an SOP (standard operating procedure) to setup (or re-setup) my MacBook after the service. Thus, I decided to document this process here.

Please notice this guide is opinionated. The following philosophical rules are enforced:

- **Be stingy**: install the minimal set of tools you need. Whenever a new software is installed, a new potential vulnerability is introduced.
- **Be Apple's fan**: use tools provided by Apple by default (opt to an external tool only when absolutely necessary). For example, we use [iTerms 2](https://www.iterm2.com) rather than the [default terminal](https://support.apple.com/guide/terminal/welcome/mac
). However, we would stick with the default [bash](https://www.gnu.org/software/bash/) and never use [zsh](http://www.zsh.org).

## Steps

1. Create a new user account on MacOS:
    - This should be done when you turn on your device for the first time;
    - Set this account as an `administer`;
    - The `full name` field should be your full real name in English (use a single space to separate each word, first letter of which should be captialized);
    - The `account name` field should be your first name in English (all lowercase, alphanumeric only);
    - Do not leave the `password` blank;
    - Do not leave the `hint` field blank as well.
2. If this is not the first time you turn on the device, and you want to change the name of your account:
    - Log into the admin account;
    - Open `System Preferences` -> `Users & Groups`;
    - Click the lock icon and enter admin password;
    - Click the plus icon to create a new account;
        - Follow the instructions in Step 1.
    - Log out and then log into the account created just now;
    - Delete the old account;
    - Go to `System Preferences` -> `Sharing`, change your bluetooth name;
        - Decide whether you want to delete that account's home folder.
    - Alternatively, see this [guide](https://support.apple.com/en-us/HT201548) from Apple for more details.
3. Now, you should have signed in with the "right" admin account. Go to `System Preferences` -> `Users & Groups` and:
    - Make sure there is only one account (the one you are using now), except for at most one guest account;
    - Change the profile picture of the current account.
4. Connect to your favorite WiFi network.
5. Everything is done with account part. Now, re-open `System Preferences` and:
    - Go to `Language & Region`, change `first of the week` to Monday and tick the `24 hours`;
        - You may want to change the language here. If so, restart the device after the change.
    - Go to `iCloud`, log into your Apple iCloud account;
        - It is important to do this step here, since this will sync your personalized data to this device.
    - Go to `Dock`, un-tick `Show recently used applications`;
    - Go to `Mission Control` -> `Hot Corners`, set the right-bottom corner to trigger sleep;
    - Go to `Security & Privacy` -> `Firewall`, turn on the firewall;
    - Go to `Display` -> `Night Shift`, turn on and choose 01:00 - 07:00;
    - Go to `Keyboard` -> `Input Method`, select Chinese Pinyin and English;
    - Go to `Date & Time` -> `Clock`, tick to show date.
6. You may need to re-start the device now.
7. Open the `Safari` browser and:
    - Verify the favourite items are synced correctly;
    - Go to the following websites and sign in on this device for the fist time:
        - Google, Facebook, LinkedIn, GitHub, Outlook, Amazon, ...
        - You may need to have either your Phone, Google Authenticator or [Authy](https://authy.com) with you for 2FA purpose.
    - Open Safari `Preferences`:
        - Go to `Privacy`, tick no tracking scripts;
        - Go to `Advanced`, tick show development menu item.
    - Install the following plugin for Safari browser:
        - AdBlock for Safari, Octotree (see [here](https://georgegarside.com/blog/macos/install-any-safari-extension-macos-mojave/)), ...
        - Add a [Personal Access Token](https://github.com/settings/tokens) for Octotree.
    - Re-open the Safari browser after that.
8. Open `Finder` -> `Preferences` and:
    - Go to `General` and select `<account name>` when opening a new Finder window;
    - Go to `Sidebar` and tick `<account name>`;
    - Go to `Advanced` and tick show all extensions, remove items in trask after 30 days and show folders on the top.
9. Open `Others` -> `Terminal` and install [Homebrew](https://brew.sh) (the package manager) and Homebrew Cask:
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap caskroom/cask
```
10. Install [iTerm 2](https://www.iterm2.com) using Homebrew `brew cask install iterm2`:
    - Drag iTerm 2 to the Dock for convenience;
    - Close the terminal and open iTerm 2 instead;
    - Open `iTerm 2` -> `Preferences`:
        - Go to `General`, tick `Quit when all windows are closed`;
        - Go to `Profiles` -> `Default` and:
            - Go to `Colors` -> `Color Presets`, select `Solarized Dark`;
            - Go to `Text`, select `Blinking cursor` and change font size to 13;
                - We suggest to use Meslo LG for Powerline - Regular (download from [here](meslo_powerline_regular.ttf)).
            - Go to `Window`, change `Transparency` and `Blur` to an an appropriate value.
    - Go to `Shell` -> `Broadcast Input` and select `Show Background Pattern Indicator`;
    - Make iTerm 2 to be the default terminal;
    - Set the tab complete to be case-insensitive `echo 'set completion-ignore-case on' >> ~/.inputrc`;
    - Make sure your bash shell is colorful `echo 'export CLICOLOR=1' >> ~/.bash_profile`;
    - Make sure your Vim is colorful as well `curl -fsSL https://raw.githubusercontent.com/yunpengn/MacBook/master/.vimrc -o ~/.vimrc`;
11. Configure your local SSH client:
    - Create a new SSH key `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`.
    - See your public key by `cat ~/.ssh/id_rsa.pub`;
    - Create a file at `~/.ssh/config` and add commonly used server configurations inside, in the following format:
```bash
Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentityFile ~/.ssh/id_rsa

Host <server-name>
    HostName <ip_address_or_domain_name>
    IdentityFile ~/.ssh/id_rsa
    User yunpengn
```
12. Install [Google Chrome](https://www.google.com/chrome/) using Homebrew `brew cask install google-chrome`:
    - Drag Chrome to the Dock for convenience;
    - Install the following plugin for Chrome:
        - AdBlock, Octotree, ...
    - Open `Chrome` -> `Preferences` and:
        - Show `Home` button and set homepage to `https://www.google.com.sg/`;
        - Use web service to detect spelling errors;
        - Send `No Tracking` requests;
        - Enable `Developer Mode` for extensions.
13. Install [Sublime Text](https://www.sublimetext.com) using Homebrew `brew cask install sublime-text`:
    - Drag Sublime to the Dock for convenience;
    - Go to `Tools` -> `Install Package Control`.
14. Install [Cyberduck](https://cyberduck.io) using Homebrew `brew cask install cyberduck`:
    - Add the commonly used SSH servers;
    - You can install [Filezilla](https://filezilla-project.org) instead.
15. Create a `Projects` folder by `mkdir ~/Projects`.
    - Later, you can clone your repositories to here.
16. Configure your local git name & email `git config --global user.name/email "<value>"`.
17. Install the following applications from App Store:
    - Onedrive, QQ, WeChat, ...

### Java Development Environment

1. Install the latest version of Oracle JDK by `brew cask install oracle-jdk`.
    - We don't use an older version of Java because we prefer latest features. However, it is permitted to use the LTS version if the latest one is not;
    - We don't use OpenJDK because previous experiences show that it could cause issues such as missing certificate.
2. Install [IntelliJ IDEA](https://www.jetbrains.com/idea/) Ultimate by [JetBrains](https://www.jetbrains.com) by `brew cask install intellij-idea`.

### Node.js & ECMAScript Development Environment

1. Install the latest version of Node.js runtime by `brew install node`.
2. Install [WebStorm](https://www.jetbrains.com/webstorm/) by [JetBrains](https://www.jetbrains.com) by `brew cask install webstorm`.

### Swift Development Environment

1. Install Xcode (bundled with Swift, iOS & macOS SDK) from App Store.
2. Go to `Xcode` -> `Preferences`:
    - Go to `Accounts`, sign into your Apple ID (bundled with Apple Developer account);
    - Go to `Navigation`, select `Uses Focused Editor` as `Navigation` option.

### Python Development Environment

1. Install the latest version of Python 3 by `brew install python3`.
    - At the time of writing, MacOs still by default comes with Python 2.7, which we would not prefer to use.
2. Install [PyCharm](https://www.jetbrains.com/pycharm/) by [JetBrains](https://www.jetbrains.com) by `brew cask install pycharm`.
3. Install [Pipenv](https://github.com/pypa/pipenv) by `brew install pipenv`.
    - We believe Pipenv is better than the others, such as [virtualenv](https://github.com/pypa/virtualenv), [pip](https://pypi.org/project/pip/), etc.

### Go Development Environment

1. Install the latest version of Go by `brew install go`.
2. Install [GoLand](https://www.jetbrains.com/go/) by [JetBrains](https://www.jetbrains.com) by `brew cask install goland`.

### MySQL Development Environment

1. We don't use other SQL servers. MySQL is the only choice for now.
2. Install the latest version of MySQL server by `brew install mysql`.
3. Start the MySQL instance at the background via `brew services start mysql`.
3. Secure the MySQL instance with `mysql_secure_installation`:
    - We recommend to use the same password as MacOS login password;
    - For local development, it is fine to not use the `VALIDATE PASSWORD` component;
    - After that, you can login as `root` with `mysql -u root -p` (for password prompt).
4. Create a new MySQL user with the **same** username as MacOS account:
    - We give all privileges to this account. However, we only allow login from localhost;
    - Login as `root` with `mysql -u root -p`;
    - Create a new user by `CREATE USER '<username_here>'@'localhost' IDENTIFIED BY '<password_here>';`;
    - Grant all privileges by `GRANT ALL PRIVILEGES ON *.* TO '<username_here>'@'localhost';`;
    - You can try to login now with `mysql -p`.
5. Install a MySQL client with GUI, [Sequel Pro](https://www.sequelpro.com) by `brew cask install sequel-pro`.

### Latex Writing Environment

1. Download [MikTex](https://miktex.org/) from [here](https://miktex.org/download).
    - Different from most online guides, we do NOT use [MacTex](http://www.tug.org/mactex/);
    - Make a private installation so that MikTex is only accessible to the current user;
    - Add the folder `~/bin/` to the current user's path variable.
2. Make sure the latest version of [Sublime Text 3](https://www.sublimetext.com) has been installed on your laptop.
    - There is no need to install any extra package(s) because [LatexTools](https://github.com/SublimeText/LaTeXTools) is shipped together with Sublime in the recent versions.
3. Create a build system for Latex by `Tools -> Build System -> New Build System...`:
```json
{
    "shell_cmd": "pdflatex \"${file}\""
}
```
4. Optionally, you may want to install [Skim](https://skim-app.sourceforge.io/) for reverse search capability.

## Licence

[GNU General Public Licence 3.0](LICENSE)
