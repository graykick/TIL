# webFaceBook SDK/API

facebook로그인을 web에 적용하는 과정이다.

1. app id 발급
2. react-facebook-login 사용.

### facebook 로그인으로 회원가입하기
fb로그인을 사용하더라도 개인당 조금이라도 다른 서비스를 제공해야 한다면, 회원가입을 해서 회원의 정보를 DB등에 저장하여 관리하여야 한다.
웹의 경우 fb로그인을 javascript를 사용하여 클라이언트에서 진행하는 경우가 많은데, 이럴경우 조금 난처해진다.
이때, 클라이언트에서 로그인한 유저의 access Tocken을 서버에 전송한뒤, 회원가입에 대한 처리을 서버에서 진행하면 된다.
