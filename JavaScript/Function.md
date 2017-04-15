# Function

함수는 객체이다. 실행가능한 객체이다. Function()에 의해 만들어진다.
함수의 사용방법은 생성한 함수에 ()를 붙여 사용한다.

js에서는 함수를 일반 객체처럼 사용할 수 있다.
함수의 인자로 넘길수 있고, 변수에 저장가능하다.
함수를 return시킬 수도 있다.

또한 함수는 생성자에 의해 생성되는 **객체** 이다.


## 함수 생성방법
1. 함수표현식
```
function boom(target) {
    target.explosion();
}
let target = new Target();
boom(target);
```
위와같이 ```function```키워드를 사용하여 생성한다. <br>
이는 **함수표현식** 이라고도 한다. 함수표현식의 경우 js엔진이 우선적으로 해석하므로, 선언순서에 구애받지 않고, 코드 어디서든 호출하여 사용할 수 있다.
반대의 경우를 **함수선언식** 이라고 한다.

2. 함수선언식
```
let boom = function (target) {
    target.explosion();
}
let target = new Target();
boom(target);
```
위와같이 ```function```키워드를 사용하여 익명함수로 생성한다. <br>
이는 **함수선언식** 이라고도 한다. 함수표현식의 경우 함수표현식과는 다르게 선언순서에 영향을 받는다. 호이스팅에 의하여 함수를 할당하려는 변수는 호이스팅 되지만, 초기화는 아직되지 않아서, 변수가 초기화되기 이전에 함수를 사용하려고 할 경우, 오류가 발생한다. 초기화 전의 변수는 undefined이다.

3. Function() 생성자
```
let boom = new Function('target', '  target.explosion()');
```
위와같이 ```Function()``` 생성자를 통해서도 함수를 생성할 수 있다.
함수표현식과 함수선언식모두 내부적으로는 ```Function()``` 생성자를 통해 생성된다.

### 함수의 속성들

1. arguments <br>
함수는 암묵적으로 ```arguments```라는 유사배열을 받는다.
이것을 통해 받은 인자에 접근할 수 있다.
```arguments``` 를통해 오버로딩을 구현할 수도 있다.
자세한 것은 //arguments

2. name <br>
함수의 이름이다.

3. caller  <br>
자신을 호출한 함수의 이름이다.

4. length <br>
함수에 정의된 매개변수의 갯수이다.

5. __proto__ <br>
모든 객체는 __proto__ 속성을 가지고 있다.
이는 객체의 prototype object를 가리킨다.
함수의 경우 Function.prototype을 가리킨다.

6.prototype <br>
prototype 속성은 함수객체만 가지고 있는 속성이다.
해당 함수가 생성자 함수로 이용될 때, 쓰인다.
해당 생성자 함수에 의해 생성될 객체의 prototype 객체를 의미한다.

즉 아래의 코드를 보자
```
function Person(name) {
    this.name = name;
}

let momo = new Person('momo');

momo.__protp__ == Person.prototype; //이는 true이다.
```
