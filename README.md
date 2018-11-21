# react-native-gvr
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fduyluonglc%2Freact-native-gvr.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fduyluonglc%2Freact-native-gvr?ref=badge_shield)


## Getting started

`$ npm install react-native-gvr --save`

### Mostly automatic installation

`$ react-native link react-native-gvr`

### Manual installation


#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-gvr` and add `RNGvr.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNGvr.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import com.reactlibrary.RNGvrPackage;` to the imports at the top of the file
  - Add `new RNGvrPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-gvr'
  	project(':react-native-gvr').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-gvr/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-gvr')
  	```
## Setup
#### iOS 

- Copy `./node_modules/react-native-gvr/pod_post_install.sh` to ios folder

- Create a **Podfile** in ios folder

```shell
target 'myProject' do
  pod 'GVRSDK'
  # Your 'node_modules' directory is probably in the root of your project,
  # but if not, adjust the `:path` accordingly
  pod 'React', :path => '../node_modules/react-native', :subspecs => [
    'Core',

    'RCTActionSheet',
    'RCTAnimation',
    'RCTGeolocation',
    'RCTImage',
    'RCTLinkingIOS',
    'RCTNetwork',
    'RCTSettings',
    'RCTText',
    'RCTVibration',
    'RCTWebSocket',
    'BatchedBridge',

  
    'DevSupport' # Include this to enable In-App Devmenu if RN >= 0.43
    
    # Add any other subspecs you want to use in your project
  ]
  
    # Explicitly include Yoga if you are using RN >= 0.42.0
  pod 'Yoga', :path => '../node_modules/react-native/ReactCommon/yoga'

  # Execute every pod install
  post_install do |installer|
      system(". ./pod_post_install.sh")
  end
end

```

Still in ios folder install pods locally

```shell
pod install 
pod update
```

- Open `myProject.xcworkspace` and under `myProject` > `Build Settings` under `Build Options` set **ENABLE BITCODE** to **NO**

### Android
- Open `./android/app/build.gradle` then set `minSdkVersion 19`

## Usage
```javascript
import { VideoView } from 'react-native-gvr'

<VideoView
  style={{ height: 300, width: 200 }}
  source={{
    uri: 'https://raw.githubusercontent.com/googlevr/gvr-ios-sdk/master/Samples/VideoWidgetDemo/resources/congo.mp4',
    type: 'mono'
  }}
  displayMode={'embedded'}
  volume={1}
  enableFullscreenButton
  enableCardboardButton
  enableTouchTracking
  hidesTransitionView
  enableInfoButton={false}
/>
```


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fduyluonglc%2Freact-native-gvr.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fduyluonglc%2Freact-native-gvr?ref=badge_large)