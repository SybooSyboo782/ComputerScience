# Access Control(접근 제어)

## 쿠키란?
- 해당 접속 정보를 클라이언트에 저장한다. 사용자가 임의로 변조하는 등 악용될 가능성이 있다.
- 쿠키는 클라이언트의 상태 정보를 로컬에 저장했다가 찾모한다.
- 클라이언트에 300개까지 쿠키 저장이 가능하고, 하나의 도메인 당 20개의 값만 가질 수 있다.
  - 하나의 쿠키값은 4KB 까지 저장 가능하다.
- Response Header 에 Set-Cookie 속성을 사용하면 클라이언트에 쿠키를 만들 수 있다.
- 쿠키는 사용자가 따로 요청하지 않아도 브라우저가 Request 시에 Request Header에 넣어서 자동으로 서버에 전송한다.

### 쿠키 사용 절차
1. 쿠키를 생성한다.
2. 해당 쿠키의 만료 시간을 설정한다.
3. 응답 헤더에 쿠키를 담는다
4. 응답한다.

### 쿠키의 제약사항
1. 쿠키의 이름은 ASCII 문자만을 이용해야 한다.
2. 한번 설정한 쿠키의 이름은 변경할 수 없다.
3. ASCII 코드에 해당하지만 공백 문자와 일부 특수문자는 사용할 수 없다.([] () = , " \ ? @ : ; )

## 세션이란?
- 해당 접속 정보를 접속중인 웹 서버에 저장한다. 쿠키에 비해 보안적으로 안전하지만 서버의 자원을 소모한다는 단점이 있다.
- 몇번을 요청하더라도 항상 같은 주소를 반환한다.
- 브라우저당 1개의 세션이 있다
- 세션은 저장소 역할을 수행하고 이 세션의 위치를 찾기 위한 id 값이 있다.
- 보통 로그인 할 때 많이 쓰지만 3세대 웹에서 서블릿을 사용하더라도 같은 세션 저장소를 공유해서 쓸 수는 있지만 응답을 json으로 하고 서버 바깥에서 동작하는 것이라 세션 공간에 접근할 수가 없다.
- 그리고 서버가 증설이 되면 톰캣이 여러 개가 되어 같은 공간을 쓸 수 없어진다.
- 중간에 로드 밸런서를 두어 1서버를 요청할 때 라운드 로빈이라는 설정을 사용한다.


### 쿠키와 세션의 공톰점
- 웹 통신 간 유지하려는 정보를 저장하기 위해 사용하는 것

## 쿠키와 세션의 차이점
1. 세션이 보안면에서 조금 더 우수하다.
   - 쿠키는 로컬에 저장되어 변질 우려가 있다.
   - 세션은 서버에서 처리하여 그나마 보안성이 높다
2. 만료기간
   - 쿠키는 만료기간의 설정이 가능하다.
   - 세션은 사이트 종료시 만료된다.
3. 쿠키가 속도면에서 우수하다.
   - 서버와의 직접 통신 없이 로컬에 저장되어 쿠키가 속도가 빠르다.
   - 세션은 서버와의 통신을 해야되어 속도가 쿠키보다 느리다.

### 토큰이란?
- 인증을 위해 사용되는 암호화된 긴 문자열

### JWT란?
- 클라이언트와 서버 통신시 권한 인가를 위해 사용하는 Json 형태의 토큰이다.
- 웹 서버의 경우에는 http나 url 헤더에 넣어서 전달하는게 가능하다.