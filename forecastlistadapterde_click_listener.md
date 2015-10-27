# ForecastListAdapter的click listener

在前面一章，我这么艰苦地写了click listener的目的就是更好的在这一章中进行开发。然而现在是时候把你学到的东西用到实践中去了。我们从ForecastListAdapter中删除了listener接口，然后使用lambda代替：

```kotlin
public class ForecastListAdapter(val weekForecast: ForecastList,
								 val itemClick: (Forecast) -> Unit)
```

