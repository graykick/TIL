# Progress Tag
음악재생 관련 React 오픈소스를 보던 중, progress라는 것을 보았는데, 아무리 찾아보아도 progress component는 찾을 수 없었다.

그도 그럴것이 progress는 개발자가 정의했던 component가 아니라, HTML의 Tag였다.

사용방법은 무척 간단하다.
```
<progress value="22" max="100"></progress>
```
value와 max값을 지정해 주면 된다. 이를 진행시키고 싶다면, value값을 수정하면 된다.
