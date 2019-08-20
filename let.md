<h4>let apply run with</h4>
<h5>1. let()</h5>
let함수를 사용하면 널이 될 수 있는 식을 더 쉽게 다룰 수 있다.<br>
let 함수를 ?. 연산자와 함께 사용하면 원하는 식이 null인지 검사 후 그 결과를 변수에 넣는 작업을 한꺼번에 처리할 수 있다. <br>
가장 흔하게 사용하는 예는 널이 될 수 있는 값을 널이 될 수 없는 값만 인자로 받는 함수에 넘기는 경우이다.<br>
예를 들어 이메일을 보내는 sendEmailTo 함수가 이메일 주소를 String 파라미터로 받는다.

~~~java
fun sendEmailTo(email : String) { }
~~~

인자인 email에는 널이 될수 있는 값은 넘어갈 수 없다.<br>
인자를 넘기기 전에 null check 후 메소드를 호출한다

~~~java
if(email!= null) {
  sendEmailTo(email)
}
~~~
이 구문을 null check 후 let 함수를 적용하면

~~~Java
email?.let { email ->
  sendEmailTo(email)
}
~~~

let함수를 통해 <u>인자를 전달</u>할 수 있다. <br>
let함수는 자신의 수신객체를 람다로 넘긴다. 람다로 전달받은 수신객체는 따로 이름을 명명하지 않으면 default name은 it이 된다. <br>

<let을 사용해야 하는 케이스>
-함수를 호출한 객체를 인자로 받고, 이를 사용하여 다른 메소드를 실행하거나 연산을 수행할 때
-한번만 생성되고 사용하지 않는 변수가 있다.

~~~java
//커스텀 뷰에서 padding 값을 지정할 때
val padding = TypedValue.applayDimension(
TypedValue.COMPLEX_UNIT_DP, 16dp, resource.displayMetircs).toInt()
//왼쪽, 오른쪽 padding 설정
setPadding(padding, 0, padding, 0)
~~~

여기에서 padding이라는 상수 값은 한번만 적용 되고 재사용되지 않는다.
이런 경우 let을 사용하면 불필요한 선언을 방지할 수 있다.

~~~java
TypedValue.applayDimension(
TypedValue.COMPLEX_UNIT_DP, 16dp, resource.displayMetircs).toInt.let {
  padding -> setPadding(padding, 0, padding, 0)
}
~~~

-아주 긴 식이 있고 그 값이 null이 아닐 때 수행해야 하는 로직이 있을 때

~~~JAVA
val person : Person = getTheBestPersonInTheWorld()
if(person != null) sendEmailTo(person.email)
~~~

이것을 let함수를 적용하면

~~~JAVA
getTheBestPersonInTheWorld?.let(sendEmailTo(it.email))
~~~

만약 getTheBestPersonInTheWorld가 null을 반환한다면 이 식은 절대 실행되지 않는다.
let을 중첩시켜 처리하면 코드가 복잡해져 가독성의 문제가 생기기 때문에, 그런 경우 if문으로 처리하는게 낫다.
