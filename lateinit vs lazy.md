
kotlin에서는 변수 선언 시 초기화를 해줘야 한다. <br>
하지만 안드로이드 개발을 할 때는 초기화를 나중에 할 경우가 있다.

<h5>lateinit</h5>
이 때는 lateinit 키워드를 변수 선언 앞에 추가 한다.
만약 lateinit 키워드를 적용 후 초기화를 잊는다면 null이 떨어져 앱이 종료될 수 있어 주의한다.

~~~JAVA
lateinit var a : String
a = "hello"
~~~

<h5>lateinit을 사용할 수 있는 조건 </h5>
1. var(mutable) 변수에만 사용한다.<br>
2. null 값으로 초기화할 수 없다.<br>
3. 초기화 전에는 변수를 사용할 수 없다.<br>
4. int, Long, Double, Float에는 사용할 수 없다.

<h5>lazy로 늦은 초기화</h5>
val(immutable)변수의 값을 변경할 때 사용한다.

lazy 초기화는 기존 val 변수 선언에 by lazy를 추가 함으로 lazy{}에 생성과 동시에 값을 초기화한다.

~~~java
public fun <T> lazy (initializer : () -> T) : Lazy<T> =
  synchronizedLazyImpl(initializer)
~~~

lazy패턴을 사용하면 thread Safe하게 동작할 수 있다.


~~~java
val sampleAdapter : SampleAdapter by lazy {
  SampleAdapter(ImageLoaderAdapterViewModel(this,3))
}
~~~


<h5>lazy를 사용할 수 있는 조건</h5>
1. 호출 시점에 by lazy 정의에 의해서 초기화를 진행한다.<br>
2. val에서만 사용 가능하다.<br>
3. val이므로 값 교체는 불가능하다<br>
4. lazy을 사용하는 경우 기본 synchronized로 동작한다.
