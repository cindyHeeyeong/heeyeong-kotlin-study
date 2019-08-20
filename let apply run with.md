<h4>let apply run with</h4>
<h5>1. let()</h5>
let함수를 사용하면 널이 될 수 있는 식을 더 쉽게 다룰 수 있다.<br>
let 함수를 ?. 연산자와 함께 사용하면 원하는 식이 null인지 검사 후 그 결과를 변수에 넣는 작업을 한꺼번에 처리할 수 있다. <br>
가장 흔하게 사용하는 예는 널이 될 수 있는 값을 널이 될 수 없는 값만 인자로 받는 함수에 넘기는 경우이다.<br>
예를 들어 이메일을 보내는 sendEmailTo 함수가 이메일 주소를 String 파라미터로 받는다.<br>
```java
fun sendEmailTo(email : String) { }
```
