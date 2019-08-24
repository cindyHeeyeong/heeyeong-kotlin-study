1. flatMap : 데이터를 변경해줌
ex ) disposable.add.
     flatMap {
       Observable.just(it)
     } -> disposable로 온 데이터를 Observable형태로 바꿔준다.


2. Subject란?
    * Observerble이 상태를 스스로 갱신하는 방식이라면, subject는 상태가 다른 객체로 부터 갱신되는 방식이다.
    * Observable은 subscribe를 통해 바로 발행되어 실행되지만, subject는 일단 대기상태에 있고, subscriber에게 데이터 변경을 통지해준다.
