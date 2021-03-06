## Cordova 环境配置

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

- 2  如果出现以下错误 可以尝试在 命令后面追加  --nofetch

```
$ cordova platform update android
Using cordova-fetch for cordova-android@~6.2.2
Error: Failed to fetch platform cordova-android@~6.2.2
Probably this is either a connection problem, or platform spec is incorrect.
Check your connection and platform name/version/URL.
Error: cmd: Command failed with exit code 1 Error output:
module.js:472
    throw err;
    ^

Error: Cannot find module 'C:\developtools\nodejs\node_modules\npm\bin\npm-cli.js'
    at Function.Module._resolveFilename (module.js:470:15)
    at Function.Module._load (module.js:418:25)
    at Module.runMain (module.js:605:10)
    at run (bootstrap_node.js:423:7)
    at startup (bootstrap_node.js:147:9)
    at bootstrap_node.js:538:3
```

追加后
```
$ cordova platform update android --nofetch
Updating android project...
Subproject Path: CordovaLib
Android project updated with cordova-android@6.2.3
--save flag or autosave detected
Saving android@~6.2.3 into config.xml file ...
```

- 3 Mac OSX 权限问题 运行 cordova build android 时报错 Error: spawn EACCES
```
➜  conditioner-app git:(dev) cordova build android
ANDROID_HOME=/Volumes/MAC-DISK/DeveloperTools/Android/sdk
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_112.jdk/Contents/Home
Subproject Path: CordovaLib
Error: spawn EACCES
```
出现这种情况时 应该 加命令参数 cordova build android --verbose 再次编译时会显示出错位置 

```
略。。。。
ANDROID_HOME=/Volumes/MAC-DISK/DeveloperTools/Android/sdk
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_112.jdk/Contents/Home
Subproject Path: CordovaLib
Running command: /Users/longyuan/WebstormProjects/conditioner/conditioner-app/platforms/android/g
radlew cdvBuildDebug -b /Users/longyuan/WebstormProjects/conditioner/conditioner-app/platforms/an
droid/build.gradle -Dorg.gradle.daemon=true -Dorg.gradle.jvmargs=-Xmx2048m -Pandroid.useDeprecate
dNdk=true
Error: spawn EACCES
```
例如我这里显示 执行到 /Users/longyuan/WebstormProjects/conditioner/conditioner-app/platforms/android/gradlew 权限异常
那么使用 
```
chmod 777 platforms/android/gradlew
```
修复权限

继续编译  正常通过 如果这里继续报错 重复以上动作



