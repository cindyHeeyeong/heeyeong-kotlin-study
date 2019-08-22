
<h5>with</h5>

~~~java
inline fun <T, R> with(receiver : T, block : T.() -> R) :R {
  return receiver.block()
}
~~~

정의에서 receiver가 수신 객체, block이 수신 객체 지정 람다이다.

with를 사용하면 반복되는 부분의 코드를 줄일 수 있다.

~~~kotlin
class Person {
  var name : String ?= null
  var age : Int ?= null
}

val person: Person = getPerson()
print(person.name)
print(person.age)
~~~

다음 코드는 person의 중복 사용을 제거하기 위해 범위 지정 함수 with를 사용해보면

~~~kotlin
val person : Person = getPerson()
with(person) {
  print(name)
  print(age)
}
~~~
