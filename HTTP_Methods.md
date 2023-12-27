## HTTP

> Hyper Text Transfer Protocol

HTTP는 클라이언트와 서버 간에 데이터를 주고받을 때 사용되는 통신 규약이다.

<br />
<br />

## HTTP 메서드

HTTP 메서드란 클라이언트가 서버에게 특정 리소스에 대한 원하는 동작을 요청하는 방법을 정의한 것이다. 즉, 서버가 수행해야 할 동작을 지정하여 요청을 보내는 방법이다.

클라이언트가 원하는 동작을 나타내는 메서드를 선택하여 서버에게 요청을 전송하고, 서버는 해당 동작을 수행한 후 클라이언트에게 응답을 보내는 웹 통신의 핵심적인 역할을 수행한다.

<br />

### HTTP 메서드 종류

HTTP 메서드는 총 9가지가 있으며, 이 중 주로 사용되는 메서드는 5가지이다.

- 주요 메소드

  - GET: 리소스 조회
  - POST: 요청 데이터 처리, 주로 등록에 사용
  - PUT: 리소스를 대체(덮어쓰기), 해당 리소스가 없으면 생성
  - PATCH: 리소스 일부 변경
  - DELETE: 리소스 삭제

- 기타 메소드

  - HEAD: GET과 유사하지만, 메시지 부분(body)을 제외하고 상태 줄과 헤더만 반환
  - OPTIONS: 대상 리소스에 대한 통신 가능 옵션(메서드)을 설명
  - TRACE: 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행
  - CONNECT: 대상 자원으로 식별되는 서버에 대한 터널을 설정

<br />

### GET

> 리소스 조회

- 리소스를 조회할 때 사용한다.
- 서버에 전달하고 싶은 데이터는 쿼리 파라미터, 쿼리 스트링 등을 통해서 전달한다.
  ```
  GET /members/100?username=yoonkyoung&height=200
  ```
  <img width="464" alt="HTTP GET 요청 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/ae485440-6139-41c8-ae6e-ee78dc5462cf">

##### 데이터 조회 과정

1. 클라이언트에서 `/members/100`으로 100번 유저를 조회해서 정보를 달라고 GET 요청을 한다.
   <img width="601" alt="HTTP GET 과정1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/6f339051-5a60-4913-b2da-70d66412bb0d">

2. 서버에서는 받은 메세지를 분석해 내부의 유저 정보를 조회한 뒤 결과 Response를 만든다.
   <img width="681" alt="HTTP GET 과정2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/9fd130c2-1dc2-4e09-a025-4f49a7e9e373">

3. 서버에서 클라이어트로 응답을 해준다. 그러면 클라이언트에서 정상적으로 받으면 200 OK status를 가지며, 회원정보를 얻게 된다.
   <img width="692" alt="HTTP GET 과정3 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/3f01da69-a944-490d-a7bb-e814fbf7cc2f">

<br />

### POST

> 요청 데이터 처리

- 서버에 데이터 처리를 요청할 때 사용한다. (데이터 신규 등록, 특정 비즈니스 로직 수행 등)
- 메시지 바디를 통해 서버로 요청 데이터 전달하면 서버는 요청 데이터를 처리한다.
  <img width="470" alt="HTTP POST 요청 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/81158a64-8714-4978-a592-a272b86db8f9">
- 신규 리소스 등록 요청 처리 시 서버는 응답에 Location 헤더를 포함한다.
  <img width="529" alt="HTTP POST 응답 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/b8ef3cfe-32d8-43c9-9e7f-07c2ac4cd3f1">

#### JSON 데이터 전송 과정

1. 클라이언트는 메세지 바디에 등록할 회원 정보를 JSON 형태로 만들어 담아 서버로 전송한다.
   <img width="671" alt="HTTP POST 과정1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/9550a0d5-5996-4191-b002-40c16c71998f">

2. 서버에서는 받은 메세지를 분석해 로직 대로 처리 한다. 예를 들어 데이터베이스에 등록하고 신규 아이디를 생성한다.
   <img width="686" alt="HTTP POST 과정2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/069ebb74-661a-404c-87fd-897c7c14cfdb">

3. 신규회원에 대한 데이터를 바디에 담아서 클라이언트로 응답한다.
   <img width="537" alt="HTTP POST 과정3 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/cd4d070c-7e37-4bcc-bb57-8a45a2093fe0">

<br />

### PUT

> 리소스 대체

- 요청 메시지에 리소스가 있으면 대체하고, 없으면 새로 생성한다.

  - 동일 리소스가 있는 경우 (PUT 요청 → 리소스 대체)
  - 동일 리소스가 없는 경우 (PUT 요청 → 리소스 생성)

- 요청 시 메시지 바디에 대체할 데이터를 담아서 요청한다.
- 요청 URI에 리소스의 위치를 명확히 지정한다. (클라이언트가 리소스 식별 ← POST와 차이점)
  ```
  POST /members: 멤버 새로 추가
  PUT /members/100: 100번째 멤버 수정
  ```
  <img width="470" alt="HTTP PUT 요청 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/e6a2b1a5-0d64-45b3-a6a0-21d7fa609b29">

#### PUT 요청에 리소스가 있는 경우

1. 100번 유저의 리소스를 교체하겠다는 요청을 보낸다.
   <img width="684" alt="HTTP PUT 요청에 리소스가 있는 경우1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/cfa2067a-7644-44d9-929d-ecce92b1b5f3">
2. 기존에 데이터가 있었다면 완전히 대체된다.
   <img width="689" alt="HTTP PUT 요청에 리소스가 있는 경우2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/c4472999-e2b2-403c-9b57-fbc64d1ba6ea">

#### PUT 요청에 리소스가 없는 경우

1. 100번 유저의 리소스를 교체하겠다는 요청을 보낸다.
   <img width="678" alt="HTTP PUT 요청에 리소스가 없는 경우1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/38678706-828a-4a23-a7b9-8bd1c8a01b67">
2. 기존에 데이터가 없다면 POST 와 같이 신규로 생성한다.
   <img width="671" alt="HTTP PUT 요청에 리소스가 없는 경우2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/a427787c-2e82-4280-a5d7-67a3cc507620">

#### PUT 요청에 일부 리소스만 변경하길 원할 경우

1. age만 50으로 변경하려고 해당 데이터를 PUT으로 전달한다.
   <img width="678" alt="HTTP PUT 요청에 일부 리소스만 변경하길 원할 경우1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/75bb3219-2379-4e1c-a661-add514c8e084">

2. 기존 데이터가 완전히 대체되어 이름 데이터가 삭제된다. (이런 경우 PATCH 메소드를 이용해야 한다.)
   <img width="687" alt="HTTP PUT 요청에 일부 리소스만 변경하길 원할 경우2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/9a4c9ed2-1074-4276-b607-05cf5219ec49">

<br />

### PATCH

> 리소스 일부 변경

- 리소스의 데이터를 부분 변경할 때 사용한다.
- 요청 시 변경할 데이터를 메시지 바디에 담아서 서버에 전달한다.
  <img width="466" alt="PATCH 요청 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/78c5f68d-617f-44c5-aa7b-b585f4689883">

#### PATCH 요청에 일부 리소스만 변경하는 경우

1. age만 50으로 변경하려고 해당 데이터를 PATCH로 전달한다.
   <img width="677" alt="HTTP PATCH 요청에 일부 리소스만 변경하는 경우1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/2300725b-ff37-469a-aaa6-59db2b69f832">

2. PUT과는 다르게 회원 정보에서 age만 변경된다.
   <img width="676" alt="HTTP PATCH 요청에 일부 리소스만 변경하는 경우2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/52b95bbe-7b93-4e0e-963a-ab2385f4ba03">

<br />

### DELETE

> 리소스 삭제

- 지정된 리소스를 삭제하기 위해 사용된다.
- 삭제 시 리소스의 위치를 지정해서 요청한다.
  <img width="464" alt="HTTP DELETE 요청 예시 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/e28ccdf0-de23-4a27-b6b0-28d9ae695aa8">

##### 100번째 멤버를 제거하는 경우

1. 100번째 멤버를 제거하기 위해 DELETE로 전달한다.
   <img width="672" alt="HTTP DELETE 과정1 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/ef975ce7-8cdb-4d68-bd7b-da0b1c2b0cb4">

2. 서버에서 요청을 받고 데이터베이스의 해당 리소스를 제거 한다.
   <img width="673" alt="HTTP DELETE 과정2 (출처: 인프런 - 모든 개발자를 위한 HTTP 웹 기본지식)" src="https://github.com/prgrms-web-devcourse/FEDC5_Techo_Talk/assets/100656920/192fd929-ce4a-43e8-89ce-91675522771e">
