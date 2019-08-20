<h5>Constructor</h5>

<h6>1. Java에서의 생성자</h6>
java에서의 생성자는 매개 변수 형태로 정의한다.<br>
생성자를 여러개 두더라도 overriding을 통해 해결한다.


~~~
public class Sample {
  private String name;
  private int age;
  private String birthday;

  public Sample(String name) {
    this.name = name;
  }
  public Sample(String name, int age) {
    this.name = name;
    this.age = age;
  }
}
~~~


---
* 참고 : overloding , overriding 이란?
-오버로딩 : 같은 이름의 메소드를 여러개 가지면서 매개변수의 유형과 개수가 다르도록 만드는 것 <br>
-오버라이딩 : 상위 클래스가 가지고 있는 메소드를 하위클래스가 재정의 해서 사용한다.<br>

<br>
오버로딩 소스
```java
public class Overloading {
  void test() {
    Log.d("매개변수 없음");
  }
  void test(int a, int b) {
    Log.d("매개변수 "+ String.valueOf(a) + String.valueOf(b));
  }
}

public class test {
  public static void main () {
    Overloading o = new Overloading();

    ob.test;
    ob.test(3,5);
  }
}
```
<br>
오버라이딩(하위 클래스가 상위클래스의 메소드를 재정의해서 사용) 소스
```java
public class Employee {
  public String name;
  public int age;

  public void print() {
    Log.d(this.name + this.age);
  }
}

public class Manager extends Employee {
  String jobOfManage;

  public void print() {
    Log.d(this.name + this.age);
    Log.d(this.name + this.jobOfManage);
  }
}
```
---

<h6>2. kotlin에서 Constructor</h6>
-Constructor는 생성자의 역할을 할 수 있다<br>
-java 와의 차이점 <br>
Sample클래스를 java 스타일 대로 작성

```java
class Sample Constructor(val name : String) {
  Constructor(name : String, age : Int) : this (name)

  Constructor(name :String, age: Int, birthday : String, age : Int , birthday : String) :this(name, age)
}
```
코틀린 스럽게 다시 코딩하면 <br>


```java
class Sample (val name : String, val age : Int=0) {
  //Do nothing
}
```
위의 코드를 설명하면 default 변수 선언을 통해 2가지 생성자를 한 번에 생성 가능하다.
