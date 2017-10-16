# OSX Web Development Setup

__DEPRECATED:__ This project is no longer actively maintained, use [this](https://github.com/michaelschwobe/mac-dev-setup) instead.

> My opinionated checklist for getting my Mac up and running for web-based projects and graphic design.

<!-- MarkdownTOC -->

- [Configure OSX](#configure-osx)
  - [Homebrew](#homebrew)
  - [$PATH](#path)
  - [Node & NPM](#node--npm)
- [Applications](#applications)
  - [iTerm2](#iterm2)
  - [Sublime Text](#sublime-text)
  - [Git Tools](#git-tools)
  - [Others](#others)

<!-- /MarkdownTOC -->

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

**TIP:** One-liner for updating Homebrew and other installed packages (such as Node):

```
brew update && brew upgrade && brew doctor && brew cleanup
```

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

**TIP 1:** Manage different versions of Node with [NVM](https://www.npmjs.com/package/nvm).

**TIP 2:** Updating NPM and check for other outdated packages (_globally_):

```
npm i -g npm@latest && npm outdated -g --depth=0
```

## Applications

If you have list of applications you need and don't feel like downloading and installing them manually, try [Homebrew Cask](http://caskroom.io/). If you prefer to do it the manual way, read on.

### iTerm2

Install [iTerm2](https://www.iterm2.com/) and then install [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) via curl.

**Colors:**
Download [base16 Ocean Dark iTerm2 colors](https://raw.githubusercontent.com/chriskempson/base16-iterm2/master/base16-ocean.dark.itermcolors), go to `iTerm2 > Preferences > Profiles > Colors > Load Presets > Import`, upload the base16 file and select it as your preset.

**Fonts:**
Browse to [Powerline-patched fonts](https://github.com/powerline/fonts) and follow the installation instructions, go to `iTerm2 > Preferences > Profiles > Text > Change Font` and change both fonts to "Source Code Pro for Powerline".

Finally, in `~/.zshrc` switch the theme declaration to:

```
ZSH_THEME="agnoster"
```

Relaunch if necessary to see your changes and check if the icons are working using this command:

```
echo "\ue0b0 \u00b1 \ue0a0 \u27a6 \u2718 \u26a1 \u2699"
```

**TIP 1:** If the icons don't align perfectly, change the font size. If all else fails, adjusting the Non-ASCII Font size is simpler than trying to fix font baselines.

**TIP 2:** Want to use the commands `showFiles` and `hideFiles` to quickly toggle hidden files on or off? Add these lines to the end of `~/zshrc`:

```
# Show or hide hidden files quickly
alias showFiles='defaults write com.apple.finder AppleShowAllFiles YES; killall Finder /System/Library/CoreServices/Finder.app'
alias hideFiles='defaults write com.apple.finder AppleShowAllFiles NO; killall Finder /System/Library/CoreServices/Finder.app'
```

**TIP 3:** Add autocompletion to repetitive commands by adding your preferred zsh plugins:

```
# Add wisely, as too many plugins slow down shell startup.
plugins=(brew git git-flow npm)
```

### Sublime Text

Install [Sublime Text 3](https://www.sublimetext.com/) and [Package Control](https://packagecontrol.io/installation).

Open `Preferences > Settings - User` and _update_ the settings to include (remove older duplicate lines):

```json
"always_show_minimap_viewport": true,
"bold_folder_labels": true,
"caret_extra_bottom": 2,
"caret_extra_top": 2,
"caret_extra_width": 2,
"caret_style": "phase",
"close_windows_when_empty": true,
"draw_minimap_border": true,
"draw_white_space": "all",
"ensure_newline_at_eof_on_save": true,
"highlight_line": true,
"ignored_packages":
[
  "Vintage"
],
"indent_guide_options":
[
  "draw_active"
],
"line_padding_bottom": 1,
"line_padding_top": 1,
"overlay_scroll_bars": "enabled",
"tab_size": 2,
"translate_tabs_to_spaces": true,
"trim_trailing_white_space_on_save": true,
"word_wrap": true
```

**TIP:** Don't use a trailing comma on the last item.

**Theme & Color Scheme:**

Install one or both themes linked below (using their instructions) and use __one__ of these extra settings:

[Materialize](https://github.com/saadq/Materialize) settings:

```json
"color_scheme": "Packages/User/SublimeLinter/Material Spacegray (SL).tmTheme",
"material_theme_bold_tab": true,
"material_theme_small_statusbar": true,
"material_theme_small_tab": true,
"theme": "Material Spacegray.sublime-theme"
```

[Spacegrey Theme](http://kkga.github.io/spacegray/) settings:

```json
"color_scheme": "Packages/Theme - Spacegray/base16-ocean.dark.tmTheme",
"font_face": "Source Code Pro for Powerline",
"spacegray_sidebar_font_small": true,
"spacegray_sidebar_tree_small": true,
"theme": "Spacegray.sublime-theme"
```

**Sublime Packages:**
Additional favorites, install via Package Manager:

- Alignment
- ApacheConf.tmLanguage
- AutoFileName
- Babel
- Babel Snippets
- BracketHighlighter
- CodeComplice
- Color Highlighter
- CSS3
- CSScomb
- DocBlockr
- EditorConfig
- Emmet
- Handlebars
- jQuery
- JsFormat
- LESS
- Markdown Preview
- MarkdownTOC
- Nettuts+ Fetch
- SCSS
- SideBarEnhancements
- SublimeLinter
- SublimeLinter-contrib-eslint - **Prior to installation:** `npm install -g eslint`
- SublimeLinter-contrib-stylelint - **Prior to installation:** `npm install -g stylelint`
- Terminal

**TIP:** Want to use Sublime from the command line? Add these lines to the end of `~/zshrc`:

```
# Sublime alias
alias subl='/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl'

# Open this file (.zshrc) in Sublime
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
- [Adobe Creative Cloud](http://www.adobe.com/creativecloud.html)
- [Atom](https://atom.io/)
- [BrowserStack](https://www.browserstack.com/)
- [CodeKit](https://incident57.com/codekit/)
- [DiffMerge](https://sourcegear.com/diffmerge/)
- [Divvy](http://mizage.com/divvy/) or [Spectacle](https://www.spectacleapp.com/)
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
- [Visual Studio Code](https://code.visualstudio.com)
