<코틀린 타입 시스템의 특성>
-null이 될 수 있는 타입
-읽기 전용 컬렉션


1. null이 될 수 있는 타입
-null이 될 수 있는 타입은 프로그램 안의 프로퍼티나 변수에 null을 허용하게 만들 수 있다.
-만약 어떤 변수가 널이 될 수 있다면, 그 변수에 대한 메소드를 호출한다면 NullPointerException이 호출 된다.
-코틀린은 이런 메소드의 호출을 금지함으로써 오류를 방지한다.

Java
```java
int strLen(String S) {
return s.length();
}
```

이 함수에 null을 넘긴다면 NullPointerException이 발생한다.

만약 이 코드를 kotlin에서 작성한다면,
"이 함수가 널을 인자로 받을 수 있는가?"를 생각해봐야한다.
널을 인자로 받는 조건은
-> strLen(null)처럼 직접 null 리터럴을 사용할 경우
-> 변수나 식의 값이 실행 시점에서 null이 될 경우

만약 null을 인자로 들어올 수 없게 한다면 다음과 같이 짜야한다.

kotlin
fun strLen(s: String) = s.length
이렇게 짠 코드는 만약 인자로 null이 온다면 컴파일 시 에러를 발생시킨다.

만약 null을 인자로 들어올 수 있게 한다면 다음과 같이 짠다.
kotlin
fun strLen(s: String?) = s.length
타입 이름 뒤에 "?"를 명시한다

이것을 정리하면
Type? --> null 또는 type이 될 수 있다.



2. null이 될 수 있는 타입을 사용하는 케이스
null과 비교할 수 있다.
null과 비교하고 나면 컴파일러는 그 사실을 기억하고, null이 아님이 확실한 영역에는 해당 값을 널이 될 수 없는 타입의 값 처럼 사용할 수 있다.
