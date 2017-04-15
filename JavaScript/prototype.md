# prototype
js의 객체지향은 class의 객체지향과는 많이 다르다.
js의 객체지향을 이해하기 위해서는 prototype에 대한 이해가 필요하다.

ES6에서 class문법이 추가되기는 했지만, 내부적인 동작은 class가 아닌 prototype이다.

js의 모든 객체는 \__proto\__ 라는 속성을 가지고있는데 이것이 가리키는것이 바로 prototype 객체이다.
 \__proto\__ 속성과 prototype 속성을 잘 이해해야 한다.

 크게 3가지의 개념을 잡아야 한다.
 생성자 함수객체, prototype 객체, instance 객체

### \__proto\__ 속성
\__proto\__ 속성은 모든객체가 가지고 있다. 이는 자신객체의 부모 prototype객체를 가리킨다.

### prototype 속성
prototype 속성은 함수객체만이 가지고 있는 속성이다.
자신(생성자 함수)으로 인해 생성될 객체의 prototype 객체를 가리킨다.

### constructor 속성
constructor 속성은 prototype 객체만 가지고 있는 속성이다.
자신을 prototype 속성으로 가지고있는 함수객체를 가리킨다.

## 프로토타입 체인
객체지향에서는 상속이라는 개념이 있다. 부모객체에 있는 속성이나, 메서드에 접근할 수 있는 것이다.
js에서도 이것이 가능하다. prototype을 이용해서.
위에서 모든객체는 \__proto\__라는 속성을 가진다고 했다. 이 속성을 통해, 객체는 자신의 prototype 객체를 알 수 있다.
만약 어떤 속성이나 메서드에 접근하였는데, 자신의 객체에는 없다면, 자신객체의 prototype 객체에서 찾는다. 만약 그곳에서도 없으면 prototype 객체의 prototype 객체에서 찾는다.
이렇게 계속 prototype을 거슬러 올라가는것을 프로토탑입 체인이라고 한다.
이 체인의 끝은 항상 Object.prototype 이다.
다시말하면, 모든객체(엄밀히 말하면 모든 객체는 아닌다. \__proto\__가 null인 객체를 만들 수도 있다.)에서 Object.prototype에 있는 속성이나 메서드에 접근하여 사용할 수 있다는 말이다.

```
let momo = {
   name: 'momo'
}

// undefined를 반환하지 않는다. '[object Object]'를 반환한다.
// toString()이 Object.prototype에 정의되었기 때문이다.
momo.toString();
```

object 리터럴을 이용해 객체를 만들경우 \__proto\__ 속성은 Object.prototype이다.
이는 Obect() 생성자에 의해 만들어 졌기 때문이다.

사실 object 리터럴을 이용해 객체를 만들어도 이는 Object() 생성자로 객페를 만든것과 동일하다.
Object() 생성자라고 했다. Object() 생성자도 함수객체 이기 때문에 prototype 속성을 가진다.
이는 Object.prototype을 의미하고 아까 toString이 정의되어 있었던 곳이다. js의 상속을 이렇게 이루어 진다.

Function() 생성자를 이용한 경우에도 크게 다르지 않다. 아래의 코드를 보자.
여기서 주목할 점은 Function 함수객체 또한 Object를 상속한 객체라는 것이다.
아래의 코드를 보면 js에서 상속이 어떻게 이루어지는지 조금은 알 수 있을것이다.
```
function Person(name) {
    this.name = name;
}

let momo = new Person('momo');

momo.__proto__ == Person.prototype;
Person.constructor == Person; // 여기까지는 별다르지 않다.

momo.__proto__.__proto__ == Object.prototype;
Person.__proto__ == Function.prototype;
Function.prototype.__proto__ == Object.prototype;
```

### 상속
위의 내용을 이해했다면, js에서 상속은 생성자함수 객체의 prototype 속성만 바꾸면 된다는 것을 짐작했을 것이다.
사실이다.
```
function Parent() {
    this.parent = 'true';
}

function Child() {
    this.child = 'true';
}

Child.prototype = new Parent();
```
