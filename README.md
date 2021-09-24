# 初衷
入职新公司手握此宝典傻瓜式的构建项目环境，不用到处去找常用的第三方库等，能力有限，欢迎各路武林侠士补充。

# Android Studio

## 下载地址

[点我跳转](https://developer.android.google.cn/studio/)

## 历史版本

[点我跳转](https://developer.android.google.cn/studio/archive)

## AS实用插件

翻译：Translation

转换Databinding布局：DatabindingConvert

字节码查看：ASM Bytecode Viewer	Kotlin版本：ASM Bytecode Viewer Support Kotlin

Json自动生成类：GsonFormatPlus	Kotlin版本：JSON To Kotlin

ADB Idea： 是一个适用于 Android Studio 和 Intellij IDEA 的 Android 开发插件，可显著提升开发效率，可以卸载应用，清除应用的缓存数据，重启应用等等。
在进行 Android 开发调试的时候，经常需要把当前项目 app 的数据清空，以测试用户第一次打开 app 时的情况。
通过快捷键Ctrl+Alt+Shift+A可以快速调出菜单，然后选择对应的选项即可。

Goodle Library Version Querier：可以查看Google仓库里面依赖库的版本号，使用方法，将光标移到gradle文件里依赖配置的行上，然后按快捷键Ctrl+Alt+Q即可显示

# JDK

## 下载地址

### java8

[点我跳转](https://www.oracle.com/cn/java/technologies/javase/javase-jdk8-downloads.html)

### 其他版本

[点我跳转](https://jdk.java.net/java-se-ri/11)

# Gradle插件

[点我跳转](https://developer.android.google.cn/studio/releases/gradle-plugin.html#updating-plugin)

比如插件版本4.1.0+，所需的 Gradle 版本6.5+

# Okhttp

OkHttp 适用于 Android 5.0+（API 级别 21+）和 Java 8+

```groovy
implementation 'com.squareup.okhttp3:okhttp:4.9.0'
```

## 新版本获取

[点我跳转](https://search.maven.org/artifact/com.squareup.okhttp3/okhttp/4.9.0/jar)

# Retrofit

Retrofit requires at minimum Java 8+ or Android API 21+.

[项目地址](https://github.com/square/retrofit)

```groovy
implementation 'com.squareup.retrofit2:retrofit:2.9.0'
```

## 添加gson解析

```groovy
implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
```

## 打印日志

```groovy
implementation 'com.squareup.okhttp3:logging-interceptor:4.7.2'
```



# Rxjava

## 新版本获取

[点我跳转](https://search.maven.org/artifact/io.reactivex.rxjava3/rxjava/3.1.1/jar)

```groovy
implementation "io.reactivex.rxjava3:rxjava:3.x.y"
```

结合retrofit使用，可以直接使用

```groovy
implementation 'com.squareup.retrofit2:adapter-rxjava3:2.9.0'
```

需要用到AndroidSchedulers.mainThread()还需要导入

```groovy
implementation 'com.jakewharton.rxbinding4:rxbinding:4.0.0'
```

# Glide

**[项目地址](https://github.com/bumptech/glide)**

```groovy
dependencies {
  implementation 'com.github.bumptech.glide:glide:4.12.0'
  annotationProcessor 'com.github.bumptech.glide:compiler:4.12.0'
}
```

# aar打包

在根目录下建立aar目录存放aar文件，根目录gradle文件配置

```groovy
allprojects {
    repositories {
        google()
        jcenter()
        maven { url 'https://jitpack.io' }
        flatDir {
            //rootProject.projectDir.getAbsolutePath()即项目根目录
            //需要在项目根目录新建aar文件夹, 把aar文件放进去:
            //比如我把 xxx1.0.aar 放入aar文件夹
            dirs new File(rootProject.projectDir.getAbsolutePath() + '/aar')
        }
    }
}
需要依赖的地方添加api(name: 'xxx1.0', ext: 'aar')
```

## fat-aar

该插件提供了将library以及它依赖的library一起打包成一个完整aar的解决方案

[点我跳转](https://github.com/kezong/fat-aar-android/blob/master/README_CN.md)

# 开源框架

## java版

### UI库

图表库	**[ MPAndroidChart](https://github.com/PhilJay/MPAndroidChart)**

下拉刷新	**[SmartRefreshLayout](https://github.com/scwang90/SmartRefreshLayout)**

BRVAH(强大而灵活的RecyclerView Adapter)	**[BaseRecyclerViewAdapterHelper](https://github.com/CymChad/BaseRecyclerViewAdapterHelper)**

屏幕适配	**[AndroidAutoSize](https://github.com/JessYanCoding/AndroidAutoSize)**

谷歌流式布局	**[FlexboxLayout](https://github.com/google/flexbox-layout)**

腾讯UI库	**[QMUI](https://github.com/Tencent/QMUI_Android)**

## 图片库

支持缩放的ImageView	**[PhotoView](https://github.com/Baseflow/PhotoView)**

图片压缩	**[Luban](https://github.com/Curzibn/Luban)**

图片轮播	**[banner](https://github.com/youth5201314/banner)**

### 工具库

安卓工具类库	**[AndroidUtilCode](https://github.com/Blankj/AndroidUtilCode)**

二维码库	**[zxing](https://github.com/zxing/zxing)**

时间选择器	**[Android-PickerView](https://github.com/Bigkoo/Android-PickerView)**

日志	**[logger](https://github.com/orhanobut/logger)**

集成工具库	**[RxTool](https://github.com/Tamsiree/RxTool)**

Android 权限请求框架 **[XXPermissions](https://github.com/getActivity/XXPermissions)**

### 数据存储

腾讯	**[MMKV](https://github.com/Tencent/MMKV)**

### 视频库

视频播放器	**[ ijkplayer](https://github.com/bilibili/ijkplayer)**	其他播放器：VLCPlayer、SmartPlayer、[ExoPlayer](https://github.com/google/ExoPlayer)

**[ GSYVideoPlayer](https://github.com/CarGuo/GSYVideoPlayer)**（集成IJKplayer、ExoPlayer、MediaPlayer）

### MVVM框架

整合Okhttp+RxJava+Retrofit+Glide**[MVVMHabit](https://github.com/goldze/MVVMHabit)**

## kotlin版

创新式协程并发网络请求	 **[Net](https://github.com/liangjingkanji/Net)**

强大的RecyclerView库(包含StateLayout)	 [**BRV**](https://github.com/liangjingkanji/BRV)

一行代码构建整个应用的缺省页	 **[StateLayout](https://github.com/liangjingkanji/StateLayout)**

JSON和长文本日志打印工具	 **[LogCat](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Fliangjingkanji%2FLogCat)**

支持异步和全局自定义的吐司工具 	[**Tooltip**](https://github.com/liangjingkanji/Tooltip)

一行代码创建透明状态栏	 **[StatusBar](https://github.com/liangjingkanji/StatusBar)**

### MVVM框架

**[谷歌sunflower](https://github.com/android/sunflower)**

# Flutter

**[FlutterExampleApps](https://github.com/iampawan/FlutterExampleApps)**

**[gsy_github_app_flutter](https://github.com/CarGuo/gsy_github_app_flutter)**

# 其他

掘金翻译计划	[**gold-miner**](https://github.com/xitu/gold-miner)

jetpack组件例子	**[architecture-components-samples](https://github.com/android/architecture-components-samples)**

开源项目分类汇总	**[android-open-project](https://github.com/Trinea/android-open-project)**

自动化测试	**[appium](https://github.com/appium/appium)**

CameraX + 华为ScanKit 二维码扫描的终极解决方案：https://github.com/HMS-Core/hms-scan-demo  官网：https://developer.huawei.com/consumer/cn/hms/huawei-scankit

Android轮子哥其他开源：https://github.com/getActivity
