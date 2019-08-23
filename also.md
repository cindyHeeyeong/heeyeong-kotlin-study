<h5>also</h5>

- with, also 차이점
1. 범위 지정 함수 호출 시 수신 객체가 전달 되는 방식

  with : 수신 객체가 매개 변수 T로 제공된다.
  also : T의 확장 함수로 제공된다.

  2. 범위 지정 함수에 전달 된 수신 객체가 수신 객체 람다에 전달되는 형식

  with : 수신 객체 지정 람다가 T의 확장 함수 형태로 코드 블록 내에 수신 객체가 암시적으로 전달된다.
  also : 수신 객체 지정 람다에 매개변수 T로 코드 블록 내에 명시적으로 전달된다.

  3. 범위 지정 함수의 최종 반환 값
  
  with : 람다를 실행한 결과를 반환
  also : 코드 블록 내에 전달된 수신 객체 반


~~~java
val person : Person = getPerson().also {
  print(it.name)
  print(it.age)
}
~~~
getPerson()함수를 사용하여 사람을 검색하고 person 변수에 할당한다. person 변수에 할당하기 전에 also는 검색된 사람의 이름과 나이를 출력한다.
