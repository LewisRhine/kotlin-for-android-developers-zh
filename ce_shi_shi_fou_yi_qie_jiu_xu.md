# 测试是否一切就绪

我们想再将编写一些代码来测试Kotlin Android Extensions是否在工作。我现在还不会对这些代码做解释，但是我想要确保它们在你的环境中是正常运行的。这可能是配置中最难的一部分。

首先，打开`activity_main.xml`，然后设置TextView的id：
```xml
<TextView
    android:id="@+id/message"
    android:text="@string/hello_world"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```
然后，手动在Activity中增加一个import语句（不要担心你现在对这个还不太理解）。
```kotlin
import kotlinx.android.synthetic.activity_main.*
```
在`onCreate`中，你现在可以直接得到并访问这个TextView了。