## Cordova 环境配置

- 需要配置 ANDROID_HOME 例如
- windows
   ```
   # 新增 ANDROID_HOM
   ANDROID_HOME=D:\android\sdk
   # PATH 中新增
   ;%ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools
   ```
> 注意环境变量一定要配置正确 否则运行各种问题

## 异常记录

- 1 Error: Could not find gradle wrapper within Android SDK. Might need to update your Android SDK.

```
$ cordova build android
ANDROID_HOME=D:\android\sdk
JAVA_HOME=C:\Java\jdk1.8.0_121
Error: Could not find gradle wrapper within Android SDK. Might need to update your Android SDK.
Looked here: D:\android\sdk\tools\templates\gradle\wrapper
```
> 解决方案 去Android Studio 目录下拷贝 gradle 到   D:\android\sdk\tools\templates\ 下 如果tools没有 templates文件夹 那就新建一个
> windows 目录 C:\developtools\JetBrains\android-studio 2\plugins\android\lib\templates

- 2 

```
```
