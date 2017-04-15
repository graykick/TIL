# Call
어떤 함수를, 원하는 ```this```에 바인딩해서 할 수 있다.
함수에 ```this```를 제외한 인자도 넘길 수 있다.
```
fun.call(thisArg[, arg1[, arg2[, ...]]])
```

```call()```를 사용하는 시점은 원하는 this의 스코프에서
```
func.call(this);
```
와같이 ```this```를 인자로 넘겨 줄 수 있다.

아래와 같이 넘겨줄 수 있다.
```
func.call(this, 'first', 'twice');
```

``` call() ```는 메서드를 훔쳐서 쓸 수 도 있다.
```this```를 넘기기 때문에 다른 객체의 메서드를 마치, 자신의 객체에서 호출한것 처럼 사용할 수 있다.(사실이다...)

잘은 모르지만, 객체지향적으로는 이상한 기능같다.

```call()```를 잘 쓴 예는 더 찾아봐야 할듯

형제격의 ```apply()```이 있다.

사촌격의 ```bind()```이 있다.

참고링크
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call
