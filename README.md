# OSX Web Development Setup

My opinionated checklist for getting my Mac up and running for web-based projects and graphic design.

**Table of Contents**

- [Configure OSX](#configure-osx)
	- [Homebrew](#homebrew)
	- [$PATH](#path)
	- [Node, & NPM](#node--npm)
	- [Gulp](#gulp)
- [Applications](#applications)
	- [iTerm](#iterm)
	- [Sublime Text](#sublime-text)
	- [Git Tools](#git-tools)
	- [Others](#others)

## Configure OSX

Open Terminal and paste this line to view hidden files:

```
defaults write com.apple.finder AppleShowAllFiles TRUE && killall Finder
```

If you'd like, add a few spaces to the Dock to group Apps, 'cuz its nicer.

```
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile";}' && killall Dock
```

Download and install Xcode from the App Store, open, agree to the terms, close. Next, open Terminal and install the Command Line Tools:

```
xcode-select --install
```

### Homebrew

To make updating easier, you'll need a package manager for things like Node, Git, etc.

Install [Homebrew](http://brew.sh/):

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

And just because, run this afterwards:

```
brew update && brew doctor
```

Install gems and brew dependencies as needed (ex: rbenv).

### $PATH

next create and edit your bash profile:

```
touch .bash_profile && open -e .bash_profile
```

add the Homebrew location to your $PATH with this line:

```
export PATH="/usr/local/bin:$PATH"
```

save and close, and finally, reload using:

```
. .bash_profile
```

### Node & NPM

Install [Node & NPM](#) with Homebrew:

```
brew install node
```

Install [Gulp](http://gulpjs.com/) via NPM and other node packages as needed (grunt, bower, etc.).

**TIP 1:** Updating:

```
brew update
brew upgrade --all
```

**TIP 2:** Updating NPM outside of Homebrew:

```
npm install -g npm@latest
```

## Applications

If you have list of applications you need and don't feel like downloading and installing them manually, try [Homebrew Cask](http://caskroom.io/). If you prefer to do it the manual way, read on.

### iTerm

Install [iTerm2](https://www.iterm2.com/) and then install [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) via curl.

**Colors:**
Download [base16 Ocean Dark iTerm colors](https://raw.githubusercontent.com/chriskempson/base16-iterm2/master/base16-ocean.dark.itermcolors), go to `iTerm > Preferences > Profiles > Colors > Load Presets > Import`, upload the base16 file and select it as your preset.

**Fonts:**
Browse to [Powerline-patched fonts](https://github.com/powerline/fonts) and follow the installation instructions, go to `iTerm > Preferences > Profiles > Text > Change Font` and change both fonts to "Source Code Pro for Powerline".

Finally, in `~/.zshrc` switch the theme declaration to:

```
ZSH_THEME="agnoster"
```

Relaunch if necessary to see your changes and check if the icons are working using this command:

```
echo "\ue0b0 \u00b1 \ue0a0 \u27a6 \u2718 \u26a1 \u2699"
```

If the icons don't align perfectly, adjusting the Non-ASCII Font size is simpler than trying to fix font baselines.

**TIP:** Want to use the commands `showFiles` and `hideFiles` to quickly toggle hidden files on or off? Add these lines to the end of `~/zshrc`:

```
# Show or hide hidden files quickly
alias showFiles='defaults write com.apple.finder AppleShowAllFiles YES; killall Finder /System/Library/CoreServices/Finder.app'
alias hideFiles='defaults write com.apple.finder AppleShowAllFiles NO; killall Finder /System/Library/CoreServices/Finder.app'
```

### Sublime Text

Install [Sublime Text 3](http://www.sublimetext.com/3) and [Package Control](https://packagecontrol.io/installation).

Open `Preferences > Settings - User` and update the settings to include:

```json
"close_windows_when_empty": true,
"draw_white_space": "all",
"highlight_line": true,
"trim_trailing_white_space_on_save": true,
"word_wrap": "true"
```

**TIP:** Don't use a trailing comma on the last item.

**Theme & Color Scheme:**
[Spacegrey Theme](http://kkga.github.io/spacegray/) - follow the github link  and follow the README file to install the theme, then open `Preferences > Settings - User` and add these Spacegrey settings:

```json
"color_scheme": "Packages/Theme - Spacegray/base16-ocean.dark.tmTheme",
"font_face": "Source Code Pro for Powerline",
"spacegray_sidebar_font_small": true,
"spacegray_sidebar_tree_small": true,
"theme": "Spacegray.sublime-theme"
```

**Sublime Packages:**
Install via Package Manager:

- Alignment
- BracketHighlighter
- CSScomb
- DocBlockr
- Emmet
- Handlebars
- jQuery
- JsFormat
- LESS
- Markdown Preview
- Nettuts+ Fetch
- SCSS
- SideBarEnhancements
- SublimeCodeIntel
- SublimeLinter
- SublimeLinter-csslint - **Run prior to installation:** `npm install -g csslint`
- SublimeLinter-jshint - **Run prior to installation:** `npm install -g jshint`
- SublimeLinter-php

**TIP:** Want to use Sublime from the command line? Add these lines to the end of `~/zshrc`:

```
# Sublime aliases
alias subl='/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl'
alias zshconfig="subl ~/.zshrc"
```

### Git Tools

For unlimited FREE **public** repositories:

- Account: [GitHub](https://github.com/)
- App: [GitHub Mac](https://mac.github.com/)

For unlimited FREE **private** repositories:

- Account: [Bitbucket](https://bitbucket.org/)
- App: [SourceTree](https://www.sourcetreeapp.com/)

### Others

Other useful Applications & Tools not mentioned above:

- [1Password](https://agilebits.com/onepassword)
- [Adium](https://adium.im/)
- [BrowserStack](https://www.browserstack.com/)
- [CodeKit](https://incident57.com/codekit/)
- [Creative Cloud](http://www.adobe.com/creativecloud.html)
- [DiffMerge](https://sourcegear.com/diffmerge/)
- [Divvy](http://mizage.com/divvy/)
- [DropBox](https://www.dropbox.com/)
- [FirefoxDeveloperEdition](https://www.mozilla.org/en-US/firefox/developer/)
- [Google Chrome](http://www.google.com/chrome/)
- [Google Hangouts](https://plus.google.com/hangouts)
- [MAMP](https://www.mamp.info/en/downloads/)
- [MiroVideoConverter](http://www.mirovideoconverter.com/)
- [Mou](http://25.io/mou/)
- [Slack](https://slack.com/)
- [Spotify](https://www.spotify.com/)
- [Transmit](https://panic.com/transmit/)
- [Wunderlist](https://www.wunderlist.com/)
