## 友盟统计 cordova/phonegap插件

官方集成文档：  
<http://dev.umeng.com/analytics/h5/phonegap-doc>

整合了官方android, ios两个平台，合2为1。**iOS使用的是无IDFA版本**，如果需要IDFA版本，请自行替换src/ios目录。

如何防止应用因获取IDFA被AppStore拒绝:  
<http://bbs.umeng.com/thread-5420-1-1.html>

## 添加插件：

    cordova plugin add https://github.com/zencodex/codova-plugin-umeng.git

## 配置APPKEY和CHANNEL：

#### 1. Android

    # 修改plugin.xml
    26             <meta-data android:name="UMENG_APPKEY" android:value="替换成YOUR APPKEY" />
    27             <meta-data android:name="UMENG_CHANNEL" android:value="替换成YOUR CHANNEL"/>

#### 2. iOS

工程Classes/AppDelegate.m 文件中，添加头文件和初始化代码：

~~~
#import <UMMobClick/MobClick.h>

@implementation AppDelegate

- (BOOL)application:(UIApplication*)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions
{
    UMConfigInstance.appKey = @"替换成YOUR APPKEY";
    UMConfigInstance.channelId = @"替换成YOUR CHANNEL";
    UMConfigInstance.eSType=E_UM_GAME;//友盟游戏统计，如不设置默认为应用统计
    [MobClick startWithConfigure:UMConfigInstance];
~~~
