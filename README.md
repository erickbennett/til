# { Today I Learned }

## 7/26/2023 Random

- How to find the .app file from an iOS build

  - Xcode -> Archive -> Select Build -> Right Click and Show in Finder -> right click on .xcarchive file and choose Show Package Contents -> navigate to Product\Applications

- url for React Native to open another app

  - `const APP_URL = 'AppName://app';`

- To see a list of drives with their identifiers `diskutil list`
- to erase a drive and reformt to JHFS+ `diskutil eraseDisk JHFS+ DriveName /dev/disk7`
- to merge partitions `diskutil mergePartitions ExFat NEWDRIVE disk7s3 disk7s4`

- VS Code Shortcuts

  - cmd + k + o to open a new window
  - select text + cmd + d to select multiple matches

- to curl a GraphQL query `curl --request POST --header 'content-type: application/json' --url 'https://server.address/graphql' --data '{"query":"query version {version\n}"}'`

- JavaScript Logical OR Assignment

`x ||= y`

- if x is falsy it's value is now y

`x &&= y`

- if x is truthy it's value is now y

`x ?? = y`

- if x is null or undefined it's value is now y'

## 7/25/2023 M1 and M2 Mac React Native Setup

### Installation

- [Install Zulu Java](https://www.azul.com/core-post-download/?endpoint=zulu&uuid=671a53e7-4f57-451c-9296-5c0199f247d5)

- Install Android Studio
- Install Xcode
- Install Xcode command line tools `xcode-select --install`
- Install Homebrew (see curl url on site)
- Install Ruby `brew install ruby`

- Modify your `.zshrc` to include these references:
  `export PATH=/opt/homebrew/opt/ruby/bin:/opt/homebrew/lib/ruby/gems/3.0.0/bin:$PATH`
  (Note, you will need to change the ver of ruby for the above path)
  `export LDFLAGS="-L/opt/homebrew/opt/ruby/lib"`
  `export CPPFLAGS="-I/opt/homebrew/opt/ruby/include"`

- Install watchman `brew install watchman`
- Install libffi (this is optional if errors) `brew install libffi`
- Install ffi `gem install ffi`
- Install cocoapods `gem install cocoapods` (not, this may require sudo)

### Troubleshooting

#### Gem Update

You may have to run these commands at some point, if you get errors:
`sudo gem install -n /usr/local/bin cocoa pods`
`pod install --repo-update`

#### Rosetta M2 Issue

If you have an M2 Mac, Rosetta is not installed. If you see this error:

"Failed to launch the app on simulator, An error was encountered processing the command (domain=NSPOSIXErrorDomain, code=3):"

You may need to install Rosetta.

Note - if this line is in your pod file `config.build_settings['EXCLUDED_ARCHS[sdk=iphonesimulator*]'] = "arm64"` - if you remove it you won't need Rosetta. This was a work around for Macs still using Rosetta

check if Rosetta is installed with:
`/usr/bin/pgrep -q oahd && echo Yes || echo No`

If No, install Rosetta with:
`softwareupdate --install-rosetta --agree-to-license`

## 4/11/2022 VSCode Tricks

- to open a file in a separate window: CMD +K, then O
- top select multiple matching items: select one and press CMD + D each time to select the next one

## 4/11/2022 Android APK Install

- to install to a device:
  `$adb install -r ~/sourcefolder/theapp.apk`

- to intall to an emulator -> drag and drop

## 3/29/2022 iOS Simulator "shutdown" error

if you attempt `$npm run ios` and receive the device shutdown error, try these steps:

- erase all content and settings
- run the simulator from xcode directly -> go to the main menu and choose developer tools
- select the correct version of iPhone to run

## 11/19/2021

### Saving Size of a Finder Window

- open Finder and set size of window
- close all Finder windows
- hold down the Option key, right-click the Finder icon and select relaunch

## 10/10/2021

macOS - shift control click the bluetooth icon to reveal bluetooth options (like reset module)

## 09/15/2021

add making a static git hub file a website to TIL

https://htmlpreview.github.io/?https://github.com/erickbennett/tsu-counters/blob/main/tsu_counters.html

add to til:

double click to select a word
then press command + d to select the next instance of the word
repeat until you've selected all the ones you want
now make one change to all

## 06/25/2021

Chrome Flags

There are a host of url flags to view Chrome information and change settings. For example:

- chrome://flags
- chrome://about

## 06/3/2021

Add an applescript to mute the system input

### Step One - Create Script

- see example

### Step Two - Setup Automator

- open Automator
- make a new quick action
- set receives to no input
- add an applescript
- copy/paste from the script from step one
- save

## Step Three - Enable Script

- open system preferences security
- under accessibility add automator
- under keyboard - shortcuts - services, ensure muteToggle is checked

## 05/20/2021

- Need to change the case of a file in a git repo?
- Changed it in your editor?
- Realized git doesn't track and commit your change?

Fix:
`$git mv file.js File.js`

## 04/04/2021

- to view the git origin url `$git remote -v`

## 03/18/2021

- patch an npm package

  - create a `patches/` folder in the project root
  - copy the author's patch file into this folder
  - add a script to `package.json`
    - `"postinstall": "patch-package"`
  - to manually patch run `$npm i patch-package`
  - patch will otherwise automatically be applied when `$npm i`

- unix PS commands

  - `$top` to view the 'top' of the list of running processes
  - `$ps axjf` to display processes regardless of user in a tree view
  - `$pkill process-name` to stop a process by name

- Android Emulator Device Commands

  - `$adb devices` to display a list of connected devices
  - `$adb reboot` to restart adb
  - `$adb kill-server` kill the adb server

## 01/26/2021

- set the default formatter for VS Code
  - Search for 'formatter' in Settings
  - `Editor: Default Formatter` to set which formatter takes priority (e.g. esbenp.prettier.vscode)

* Cocoapods workaround for M1 Macs - a couple possible fixes until various development tooling is native

  - set terminal to run in rosetta (no noticeable changes for me)
  - re-install cocapods and a specific gem that is in conflict (in my case it was ffi)
    `install cocoapods`
    `sudo gem install cocoapods`
    `sudo gem install ffi`

* Next JS and GQL/Apollo Performance Reminders

  - don't use SSR unless you need it
  - avoid using Get Initial Props (and use things like router.query)
  - Next build will detect if you are relying on SSR / Get Initial Props and will create a static build automatically if you are not
  - Stop query polling with Apollo queries if the client window does not have focus (great for instances where a page or app is minimized)

* ZSH Path - to add to your PATH when using ZSH it is a simple as adding entries to your `.zshrc` file
  `export PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true`
  `export ANDROID_HOME=${HOME}/Library/Android/sdk`
  `export PATH=${PATH}=${PATH}:${ANDROID_HOME}/tools`
  `export PATH=${PATH}=${PATH}:${ANDROID_HOME}/platform-tools`

## 11/28/2019

- got one of those ext drives you can't partition? greyed out in disk util?

`$diskutil erasedisk hfs+ External GPT /dev/disk2` - where the drive is disk2

## 11/26/2019

### Open VS Code from the CLI

(been using this one for a long time but had to recently set up again)

- open the Command Palette (shift + command + p)
- enter 'shell command'
- select Install 'code' command in PATH
- from CLI `$code .` to open current folder or `$code file.name` for a specific file

### Change permissions on .config

- error message ".config/git/ignore': Permission denied"
- In Terminal cd to the User directory `$cd ~`
- Change permissions with `$sudo chmod 755 .config`
- Enter pwd

## 11/21/2019

- a quick and very easy way to switch between Node JS versions is the npm package 'n'
- to install `$sudo npm install -g n` (can also use Brew to install)
- to switch versions `$sudo n 9.11.0` -> n will either switch (if previously installed) or install that version and switch
- to view (and switch) what's available `$n`

## 9/19/2019

- if you use React snippets for VS Code... `RFAC` is the snippet for creating a functional component (using the arrow syntax)

## 7/25/2019

- not new but good to remember

```javascript
const errorStyle =
  'font-weight: bold; font-size: 32px; color: red; text-shadow: 1px 1px 0px black, 1px -1px 0px black, -1px 1px 0px black, -1px -1px 0px black;';

console.error('%c Gasp!', consoleStyle, error);

console.info(
  '%c Barely worth a mention, this.',
  'color: blue; font-size: 12px'
);

console.clear();
console.assert(buckeye > wolverine); // true
console.table(anArray);
```

- use browser sync for a quick work
- installed globally

```
$browser-sync start --server --files '*.css, *.html, *.js' --browser firefox"
```

## 5/2/2019

- Using React.Children to add props to child elements

```javascript
const newChildren = React.Children.map(this.props.children, child => {
  return React.cloneElement(child, {
    isActive: this.state.value === child.props.value,
  });
});
```

## 4/19/2019

- How to submit a form after preventing it from submitting

```javascript
e.preventDefault();
const { target } = e;
const formSubmitCallback = () => target.parentElement.submit();
```

## 4/11/2019

- properties for keeping font widths the same for 'skinny' vs 'wide' numbers

```css
p {
  font-feature-settings: 'tnum';
  font-variant-numeric: tabular-nums;
}
```

## 3/22/2019

- couple tips I've known for a while but nice to capture on the page

### Add a color to VS Code Title Bar

- great idea from Wes Bos, color the title bar based on project, frontend vs backend, etc.
- create a folder `.vscode` in the project (make sure to uncomment .gitignore)
- add a file `settings.json` to the folder
- add some customizations:

```javascript
{
  "workbench.colorCustomizations": {
    "titleBar.activeBackground": "#2ecc40",
    "titleBar.inactiveBackground": "#3d9970"
  }
}
```

### Add a link to a MD file

[Today I Learned](https://www.github.com/erickbennett/til.git)

```markdown
[Today I Learned](https://www.github.com/erickbennett/til.git)
```

## 3/15/2019

### Render Props

```javascript
// creating -> see hooks example

// implementing
<Toggle>{({ on, toggle }) => <Fancy on={on} toggle={toggle} />}</Toggle>
```

### Hooks

```javascript
import { useState } from 'react';

const Toggle = ({ children }) => {
  const [isToggled, setToggle] = useState(false);
  return children({ isToggled, setToggle });
};

export default Toggle;
```

## 3/7/2019

### Launch a specific browser with create-react-app

- package.json

```javascript
"scripts": {
    "start": "BROWSER='Firefox Developer Edition' react-scripts start"
}
```

## 3/6/2019

### React Testing

- Adding a data property to an element is a useful way to aid unit testing

```javascript
<Link to={ROUTE_DETAIL} data-testid="detail-link" />
```

### Gay Hendrick's genius move

1. Any time you **notice** any sort of unhappiness in you...
2. Ask, **what am I trying to control** that is not in my power to control
3. Sometimes you get an immediate **insight**, if not spend time thoughtfully wondering
4. Formally declare it outside of your control; let it go, let it be. Now, **think of a positive action you have control over and take it**

## 3/5/2019

### TIL

TIL is a quick way to capture learning without the time of a blog.

### Parkinson's Law

Parkinson's law of triviality _is an observation about the human tendency to devote a great deal of time to unimportant details while crucial matters go unattended._

### Using React for Presentations

- a React project for creating presentations
- [Spectacle](https://github.com/FormidableLabs/spectacle) on Github
