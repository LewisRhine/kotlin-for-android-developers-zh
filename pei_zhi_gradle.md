# 配置Gradle

Kotlin插件包括一个让我们配置Gradle的工具。但是我还是倾向于保持我对Gradle文件读写的控制权，否则它只会变得混乱而不会变得简单。不管怎么样，在使用自动工具之前知道它是怎么工作的是个不错的主意。所以这次，我们将手动去做。

首先，你需要如下修改父`build.gradle`：
```groovy
buildscript {
    ext.support_version = '23.0.1'
    ext.kotlin_version = '0.13.1514'
    ext.anko_version = '0.7'
    repositories {
        jcenter()
        dependencies {
            classpath 'com.android.tools.build:gradle:1.2.3'
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
        }
    }
}
allprojects {
    repositories {
        jcenter() 
    }
}
```
正如你看到的，我们创建了一个变量来存储当前的Kotlin版本。你读到这里的时候去检测一下最新版本，因为可能会有更新的版本已经发布了。我们需要在几个不同的地方用到那个版本号，比如你需要加上新的Kotlin插件的`dependency`。你会在你指定的那些模块中的`build.gradle`中再次需要到它。

我们对于`support library`也是如此，`Anko`库也是同样的做法。用这个方式可以更方便地在一个地方修改所有的版本号。并且使用相同的版本号，更新的时候也不需要每个地方都修改。

我们会增加`Kotlin`库，`Anko`库和`Kotlin Android Extensions plugin`到dependencies。
```groovy
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android'
android {
    ...
}

dependencies {
    compile "com.android.support:appcompat-v7:$support_version"
    compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
    compile "org.jetbrains.anko:anko-sdk15:$anko_version"
    compile "org.jetbrains.anko:anko-support-v4:$anko_version"
}

buildscript {
    repositories {
jcenter() }
    dependencies {
      classpath "org.jetbrains.kotlin:kotlin-android-extensions:$kotlin_version"
    } 
}
```
Anko库需要几个依赖。第一个是指所支持的最小的SDK。不能比你在`build.gradle`中定义的最小SDK更高，这点很重要。第二增加了额外的`support-v4`库的功能，这是导入`appcompat-v7`库时隐含增加的。


