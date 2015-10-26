# 类继承

默认任何类都是基础继承自`Any`（与java中的`Object`类似），但是我们可以继承其它类。所有的类默认都是不可继承的（final），所以我们只能继承那些明确声明`open`或者`abstract`的类：
```kotlin
open class Animal(name: String)
class Person(name: String, surname: String) : Animal(name)
```