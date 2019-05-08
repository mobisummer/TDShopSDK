# TDShopSDK iOS

README: [English](https://github.com/mobisummer/TDShopSDK/blob/master/README.md) | [中文](https://github.com/mobisummer/TDShopSDK/blob/master/README-zh.md)

## Installation

From CocoaPods

`pod 'TDShopSDK'`

## Examples(Swift)

###  `"import TDShopSDK"`

### 1.Initialization SDK
```
let config = TDConfig.config(appkey: "your appKey") { (isInitSuccess,errMsg) in
}
// You can show TDShopSDK's log ,if you set isDebug true.
config.isDebug = true
TDShopSDK.sdkInitialize(config: config)
```

### 2.URL SCHEME 

#### Step1：Add TDShopSDK scheme to Info.plist file 

scheme `tdshop`

#### Step2：Handle Applcation open url msg
```
func application(_ application: UIApplication, handleOpen url: URL) -> Bool {
     return TDShopSDK.handleOpenUrl(url: url)
}
func application(_ app: UIApplication, open url: URL, options: [UIApplication.OpenURLOptionsKey : Any] = [:]) -> Bool {
     return TDShopSDK.handleOpenUrl(url: url)
}
```
#### Step3 Use DemoLink for Test

`tdshop://mytdshop.net/195221EF4498F6F0E1CC10C852843F2643C4168F181E443552C442C50939A437`

SDK will open a ViewController witch show the google page , if success!

### 3.TDIconView 
#### TDIconView need a  Appropriate ratio (width:height 1:1)
```
let WH:CGFloat = 100
let iconView = TDIconView.init(frame: CGRect.init(x: 0, y: 0, width: WH, height: WH))
self.view.addSubview(iconView)
```
#### Add the following code in viewWillAppear
```
override func viewWillAppear(_ animated: Bool) {
    super.viewWillAppear(animated)
    self.iconView.handleWhenViewAppear()
}
```

### 4.TDBannerView 
#### TDBannerView need a  Appropriate ratio (width:height 720:372)
```
let W:CGFloat = 300
let H:CGFloat = W * 372/720.0
let iconView = TDIconView.init(frame: CGRect.init(x: 0, y: 0, width: W, height: H))
self.view.addSubview(iconView)
```
#### Add the following code in viewWillAppear
```
override func viewWillAppear(_ animated: Bool) {
    super.viewWillAppear(animated)
    self.bannerView.handleWhenViewAppear()
}
```

### 5.Show Interstitial 

```
TDShopSDK.showInterstitialView()

```
