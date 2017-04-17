# object

js의 object는 key와 value 쌍으로 이루어져 있다.

## 객체 생성방법

- ##### object 리터럴 사용

  `{}`를 사용하여 object를 생성할 수 있다.

  ```
  let obj = {
    name: 'momo',
    cute: true,
    getName: () => return this.name
  }
  ```

  object 리터럴을 사용할때는 몇가지 규칙이 있다. key값을 명시할때는 `""`이나 `''`를 사용하지 않아도 되는데 단, 몇가지 예외가 있다.

  - 예약어일경우, `""`이나 `''`로 감싸야한다.
  - js에서 변수명으로 사용할 수 없는경우 `""`이나 `''`로 감싸야한다.

- ##### Object()

  Object() 생성자를 이용해서 객체를 생성할 수 있다. 사실 object 리터럴을 사용하여 객체를 생성하는 것과 Object() 생성자를 이용해서 객체를 생성하는것은 같다. object 리터럴로 객체를 만들더라도 js 엔진을 Object() 생성자를 이용해서 객체를 만든다.

  ```
  let person = new Object();
    person.name = 'momo';
    person.cute = true;
    person.getName = () => return this.name
  ```

- ##### 객체 생성자 정의

  js의 함수를 이용해서 객체의 생성자(constructor)를 정의 할 수 있다.<br>
  js에서는 함수가 객체고 객체가 함수다.(???) 일반 함수와 구분하기 위해 대부분 생성자함수의 경우 이름이 대문자로 시작한다.

  ```
  function Person(name, gender) {
    this.name = name;
    this.gender = gender;
    this.getName = () => return this.name
  }
  ```

  여기서 `this`는 생성될 객체의 instance의 `this`이다. 이렇게 생성된 객체의 prototype 객체는 Person.prototype 이다.

- ##### Object.create()




객체에 접근할때는 `obj.key`혹은 `obj[key]`로 접슨할 수 있다. `[]`로 접근하는경우는 굉장히 유용하게 사용할 수 있다.

```
let Obj = {
    this.moveTo = {
        left: () => {
            // moveTo left
        },
        right: () => {
            // moveTo right
        }
    }

    this.move(direction) = () => {
        this.moveTo[direction]();
    }
}
```

위와같이 문자열을 받아서 해당 문자열에 해당하는 객체의 멤버에 접근이 가능하다

## 객체 멤버삭제

`delete`사용해서 삭제가 가능하다.
단, 삭제불가능한 경우가 있는데, 이는

```
let obj = {
  name: 'momo',
  cute: true,
  getName: () => return this.name
}

delete obj.cute;
```

## for in

for in문을 사용해서, 객체에 존재하는 멤버중, 열거가능한 속성들의 key를 간편히 얻을 수 있다.
```
let obj = {
  name: 'momo',
  cute: true,
  getName: () => return this.name
}

for(let key in obj) {
    obj[key]
}
```
