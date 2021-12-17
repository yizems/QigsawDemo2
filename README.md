# Qigsaw Demo

[Qigsaw](https://github.com/iqiyi/Qigsaw)

**使用版本: 1.4.1-hotfix02**

```
AGP: 4.2.2
Kotlin: 1.5.22
```

## 坑记录

### 1. AGP 7 创建的项目, 改成AGP 4.2 需要调整 版本设置

主module 和子module 都需要改
```
compileSdkVersion 31
defaultConfig {
    minSdkVersion 21
    targetSdkVersion 31
}
```
AGP 7 默认设置的是

```
compileSdk 31
defaultConfig {
    minSdk 21
    targetSdk 31
}
```

看到差别了吧, 没有后缀 Version

### 2. AGP 可以升级, 但是 buildSrc 下的 AGP 依赖不要升级

```

dependencies {
    // 这个不能升级,最好写死,和官方demo写的一样就行
    implementation "com.android.tools.build:gradle:3.4.2"
}
```
### 3. Qigsaw与viewBinding冲突
摘自: https://github.com/iqiyi/Qigsaw/issues/60
未验证

```
android {
    ...
    buildFeatures {
        ...
    }
}
改为
android {
    ...
    buildFeature {
        ...
    }
}
```



