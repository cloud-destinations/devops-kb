# Install Flutter and Android Sdk (Virtual Machine) on Ubuntu 20.04LTS without Android Studio

## Install Java 8

```bash
sudo apt install openjdk-8-jdk-headless
```
### Install the flutter package from the website
### from here https://flutter.dev/docs/get-started/install/linux
### Extract the content to ~/flutter
### export the file in .bashrc or .zshrc
cd ~
git clone https://github.com/flutter/flutter.git -b stable
export PATH="$PATH:~/flutter/bin"


## Android SDK

### Download the commandlinetools from Android Studio website https://developer.android.com/studio
```bash
mkdir -p android/sdk
unzip commandlinetools-linux-<VERSION>.zip -d android/sdk
mkdir -p android/sdk/cmdline-tools/latest
mv android/sdk/cmdline-tools/* android/sdk/cmdline-tools/latest/

export ANDROID_HOME=$HOME/android/sdk
# Make sure emulator path comes before tools. Had trouble on Ubuntu with emulator from /tools being loaded
# instead of the one from /emulator
export PATH="$ANDROID_HOME/emulator:$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$PATH"

sdkmanager "tools"

sdkmanager --update
sdkmanager --list
sdkmanager "build-tools;33.0.1" "platform-tools" "platforms;android-33" "tools"
sdkmanager --licenses
sdkmanager "system-images;android-33;google_apis_playstore;x86_64"

sudo apt update 
sudo apt upgrade
sudo apt install clang cmake ninja-build pkg-config libgtk-3-dev

Download and install chrome
https://www.google.com/chrome/thank-you.html?brand=YTUH&platform=linux&statcb=0&installdataindex=empty&defaultbrowser=0

flutter doctor


````

Note: you can get an updated Android SDK link from https://developer.android.com/studio/#downloads

Used a combinaton of these gists:
https://gist.github.com/fedme/fd42caec2e5a7e93e12943376373b7d0
https://gist.github.com/jjvillavicencio/18feb09f0e93e017a861678bc638dcb0

Background on the update to command line tools from android sdk
https://stackoverflow.com/a/61176718
