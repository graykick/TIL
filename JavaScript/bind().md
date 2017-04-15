# bind
```bind()```는 함수에 ```this```를 바인딩 한 함수를 리턴한다.
react에서도 쓰이는 예를 자주 볼 수 있다.

```
fun.bind(thisArg[, arg1[, arg2[, ...]]])
```

```bind()```가 쓰이는 이유는, 메서드를 다른 변수에 할당할 경우,
그 함수(새로 생성된)의 ```this```는 원래 메서드의 객체가 아니라,
새로운 변수에 할당할 당시 스코프의 this이기 때문이다.

예를 보자

```
let name = 'momo';

let Person = {
    name: 'sana';
    getName: function () {
        return this.name;
    }
}

Person.getName(); // 'sana';

// 메서드를 다른 변수에 할당하여 함수로 사용할 수 있도록 하였다.
let getNameOut = Person.getName;
getNameOut(); // 'momo'
```
위의 예제에서 getNameOut()을 호출했을 때, 'sana'를 return하기를 기해한 사람도 있겠지만, 그렇지않다.
'momo'를 return한다. 함수가 할당된 당시의 this로 접근한것 이다.
getNameOut를 할당할때, ```let getNameOut = Person.bind(Person)```과 같이 할당하였다면, 'sana'가 return될것이다.

사실 이러한 문제는 ES6의 arrowFunction을 사용하면 ```bind()``를 사용하지 않아도 된다.


참고링크
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind
