# setState

컴포넌트의 state를 변경하는 메서드이다. 주의할 점은 이것이 **비동기** 메서드라는 것이다. 실행즉시 변경될것이라고 기대하면 안된다. 그래서 이런식으로 setState 코드를 작성하면 곤란하다.

```
(A, B) => {
    if(A){
      this.setState({
          flag: {
              A: true,
              B: this.state.flag.B
            }
       })
     }
    if(B){
       this.setState({
         flag: {
              A: this.state.flag.A,
              B: true
            }
        })
      }
}
```

위의 코드의 경우 A, B가 참일 경우 현재 state의 flag모두가 true로 될것을 기대하고 짠 코드이지만
이는 생각대로 되지 않는다.

다시한번 setState는 **비동기**이다.
