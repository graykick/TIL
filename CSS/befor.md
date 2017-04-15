# Before

css에서 굉장히 유용하게 사용할 수 있는 가상클래스이다.
대부분 after는 ```content``` 속성을 사용하는데, 이는 해당 Element의 앞에 ```content```속성의 값을 추가한다.
이 ```content```에는 css 스타일 또한 추가할 수 있어서 굉장히 유용하게 사용될 수 있다.
html에서 추가하는것과 다른 점은 이는 드래그가 불가능 하다는 점이다.
이러한 점을 사용한 좋은 예로는 아래와 같다.

1. 항목 옆에 mark표시 (sale, soldout 등)
2. 화살표등을 after,before를 사용하여 구현한 경우도 있다.


아래의 예제는 list의 li에 bug라벨을 추가하는 예제이다.
```
li.bug:before{
  content:"bug";
  font-size: small;
  padding: 3px 6px;
  border-radius:4px;
  color: white;
  background: red;
}
```
