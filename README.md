### 所有配置地址：
1.bintray：<br>
//
<br>
2.基础build.gradle<br>
https://raw.githubusercontent.com/ihanbo/gradleBaseConfig/master/baseconfig.gradle
<br>
3.依赖管理<br>
https://raw.githubusercontent.com/ihanbo/gradleBaseConfig/master/dependencies.gradle
<br>

---


### 1.基础build.gradle:
帮做好了一些统一配置，如编译版本之类的
使用：
在`module`的`build.gradle`里：添加
```gradle
//apply plugin: 'com.android.application'
apply plugin: 'com.android.library'
apply from: 'https://raw.githubusercontent.com/ihanbo/gradleBaseConfig/master/baseconfig.gradle'
```
示例：公共部分已配好，只需配个性化的，当然也可以复写公共的
```gradle
...
android {
    defaultConfig {
	    //module的额外配置
        versionCode 1
        versionName "1.0"
        //applicationId "com.example.hans.testlauncha"
    }
}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile  "${DEP.SUPPORT.appcompatV7}"
}
```
### 2. 关于上传Bintray：
在`module`的`build.gradle`里：前面添加
```gradle
ext {
    BT_GROUP = 'com.xx.xx'
    BT_ARTIFACT = 'xxxx'
    BT_VERSION = '1.0'
    BT_DESC = '可有可无'
}
```
在`local.properties`里配置:
```gradle
bintray.user=xxx
bintray.apikey=xxx
```
### 3. 依赖配置：
在根项目(根目录)的`build.gradle`里添加：
```gradle
apply from: 'https://raw.githubusercontent.com/ihanbo/gradleBaseConfig/master/dependencies.gradle'
```
所有项目依赖版本再次统一管理，当然也可以配到`module`的`build.gradle`里
