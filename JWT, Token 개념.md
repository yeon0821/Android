# Token

토큰 기반 시스템은 무상태. 즉 상태유지를 하지 않는다는 것이다. 

이 시스템에는 유저의 인증 정보를 서버나 세션에 담아주지 않는다.

이 개념 하나만으로 위에서 서술한 서버에서 유저의 인증 정보를 서버측에 담아둠으로 발생하는 많은 문제점들이 해소 된다.

세션이 존재하지 않으니, 유저들이 로그인 되어있는지 안되어있는지 신경도 쓰지 않으면서 서버를 손쉽게 확장 할 수 있다.

----

1. 유저가 아이디와 비밀번호로 **로그인**을 합니다
2. 서버측에서 해당 **계정정보를 검증**합니다.
3. 계정정보가 정확하다면, 서버측에서 유저에게 *signed* **토큰을 발급**해줍니다.
   *여기서 signed 의 의미는 해당 토큰이 서버에서 정상적으로 발급된 토큰임을 증명하는 signature 를 지니고 있다는 것입니다*
4. 클라이언트 측에서 전달받은 **토큰을 저장**해두고, 서버에 요청을 할 때 마다, 해당 **토큰을 함께 서버에 전달**합니다.
5. 서버는 **토큰을 검증**하고, **요청에 응답**합니다.

---

## JWT이란?

사용자가 로그인을 하면 토큰을 주는데, 이 토큰을 서버가 기억하고 있지 않는다. (시간에 따라 바뀌는 어떤 상태값을 안 갖는 것 - stateless, 반대로 세션은 stateful)

- JWT 예시
- ![img](https://velog.velcdn.com/images%2Fsyoung125%2Fpost%2F22a71891-6193-4639-a997-448298dbb043%2Fimage.png)

암호화된 3가지 데이터를 이어붙인 형태(aaa.bbb.ccc)로 구성되어 있다.

###  1. Header  

- Header는 두가지의 정보를 지니고 있다.

- typ: 토큰의 타입을 지정.
- alg:  해싱 알고리즘으 ㄹ지정한다.  해싱 알고리즘으로는 보통 HMAC SHA256 혹은 RSA 가 사용되며, 이 알고리즘은, 토큰을 검들할 떄 사용되는 signature 부분에서 사용.

###   2. Paylond 

- 

## 다크 모드



## 글자 크기





## 카테고리

- -  항해99 **(69)**
    - [ TIL **(66)**](https://gorokke.tistory.com/category/항해99/TIL)
    - [ Project **(2)**](https://gorokke.tistory.com/category/항해99/Project)
  -  Java, IntelliJ **(22)**
    - [ JAVA **(7)**](https://gorokke.tistory.com/category/Java%2C IntelliJ/JAVA)
    - [ Spring **(15)**](https://gorokke.tistory.com/category/Java%2C IntelliJ/Spring)
  -  python **(15)**
    - [ Selenium 셀레니움 **(2)**](https://gorokke.tistory.com/category/python/Selenium 셀레니움)
    - [ beatifulsoup 뷰티풀스프 **(2)**](https://gorokke.tistory.com/category/python/beatifulsoup 뷰티풀스프)
  -  Algorithm(알고리즘) **(66)**
    - [ 백준 **(38)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/백준)
    - [ 기본 **(3)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/기본)
    - [ 재귀함수 **(7)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/재귀함수)
    - [ Brute Force **(3)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/Brute Force)
    - [ Divide and Conquer **(4)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/Divide and Conquer)
    - [ Quick sort 퀵정렬 **(2)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/Quick sort 퀵정렬)
    - [ Dynamic Programming **(5)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/Dynamic Programming)
    - [ Greedy Algorithm **(4)**](https://gorokke.tistory.com/category/Algorithm(알고리즘)/Greedy Algorithm)
  - [ Linux , Vim **(1)**](https://gorokke.tistory.com/category/Linux %2C Vim)
  - [ html_Ajax **(1)**](https://gorokke.tistory.com/category/html_Ajax)
  - [ html , css **(14)**](https://gorokke.tistory.com/category/html %2C css)
  - [ JavaScript **(1)**](https://gorokke.tistory.com/category/JavaScript)
  - [ 프로그램 설치 **(4)**](https://gorokke.tistory.com/category/프로그램 설치)
  - [ git **(3)**](https://gorokke.tistory.com/category/git)
  -  게임 공략 **(1)**
    - [ 발하임 공략(Valheim) **(1)**](https://gorokke.tistory.com/category/게임 공략/발하임 공략(Valheim))
    - [ 모바일 게임 공략 **(0)**](https://gorokke.tistory.com/category/게임 공략/모바일 게임 공략)

## 최근 글

- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtJpUQ%2FbtrePW3XYTX%2FIXxXe2Hth1GBb45RyulWj1%2Fimg.png)항해99 수료- 항해를 끝마치며 ( 9/11 )2021.09.12](https://gorokke.tistory.com/218)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnYHeL%2Fbtrdo9dIxv5%2Folo82hasd6DcQHcBThQYG1%2Fimg.png)프로젝트 서비스 론칭! 같이 배달 받는 서비스 밀착!2021.08.28](https://gorokke.tistory.com/217)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FE24z7%2Fbtrc8g5v9Iz%2FhxGK5SKC9H6jS7pCWTUCtK%2Fimg.png)AWS EC2_Nginx_ Let's Encrypt로 HTTPS 적용하기2021.08.27](https://gorokke.tistory.com/216)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZ8DxX%2Fbtrc1Tvv3gv%2FmZrPom7KvBUZ4hK5teiG31%2Fimg.png)JAVA 이미지 리사이징, 가로세로 크기 줄이기2021.08.24](https://gorokke.tistory.com/214)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbe5Qdn%2Fbtrcvx7pHq3%2FaXtQjjmzAO8pdcSiOVKxx0%2Fimg.jpg)72일차-8/17 화 TIL -항해99 일지2021.08.19](https://gorokke.tistory.com/213)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcGZFDo%2Fbtrcb9yUkWW%2FGJZKjYCrHRZqBNQKhoMU71%2Fimg.png)64일차-8/09 월 TIL -항해99 일지2021.08.17](https://gorokke.tistory.com/212)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbe1vCg%2Fbtrb77gM0Rv%2FVB6ewZ0lM25NsNqxBSuOvK%2Fimg.png)63일차_8/08_항해99 -9주차 WIL(회고록)2021.08.16](https://gorokke.tistory.com/211)

## 인기 글

- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FoK198%2Fbtq80yuuInd%2FkRvuk5yoXtDq0PVTB8S5HK%2Fimg.png)[Spring\]Thymeleaf Js내부에서 사용하기, 로그인 여부에 따라 보이기2021.07.06](https://gorokke.tistory.com/170)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb83546%2Fbtq9ynNspjK%2FM2QYx98gmtBv1as4OGe930%2Fimg.png)JWT토큰이란, 장단점, 구현2021.07.14](https://gorokke.tistory.com/181)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FblQI9M%2Fbtq9fwD0tNH%2FPzf2cELx3h3lGJSdOppxr0%2Fimg.jpg)네이버 클라우드 서버 1년 무료 이용하기2021.07.11](https://gorokke.tistory.com/177)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbF1Xbc%2FbtraWuiRf0E%2FknD3szM6tsJtk6HSb0eedk%2Fimg.png)SPRING,JPA 원하는 값 내려주기 방법 모음 총 정리, Projection 방법 모음2021.08.01](https://gorokke.tistory.com/202)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZ8DxX%2Fbtrc1Tvv3gv%2FmZrPom7KvBUZ4hK5teiG31%2Fimg.png)JAVA 이미지 리사이징, 가로세로 크기 줄이기2021.08.24](https://gorokke.tistory.com/214)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FE24z7%2Fbtrc8g5v9Iz%2FhxGK5SKC9H6jS7pCWTUCtK%2Fimg.png)AWS EC2_Nginx_ Let's Encrypt로 HTTPS 적용하기2021.08.27](https://gorokke.tistory.com/216)
- [![img](https://i1.daumcdn.net/thumb/S90x60/?fname=https://img1.daumcdn.net/thumb/R750x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtJpUQ%2FbtrePW3XYTX%2FIXxXe2Hth1GBb45RyulWj1%2Fimg.png)항해99 수료- 항해를 끝마치며 ( 9/11 )2021.09.12](https://gorokke.tistory.com/218)

## 최근 댓글

- [오우!~ 굿!!!~ 땡쓰 베리 감솨!!~](https://gorokke.tistory.com/11#comment21537404)
- [궁금한 내용 있으시면 물어보세요 아는 선에서 답해드릴게용 1:1 오픈카톡 https://open.kakao.com/o/sf7ugZQd](https://gorokke.tistory.com/20#comment21386624)
- [안녕하세요 혹시 개인적으로 과외를 받아볼 수 있을까요?](https://gorokke.tistory.com/20#comment21386595)
- [UserMapping 은 어떻게 구현하셨는지 궁금합니다..!](https://gorokke.tistory.com/202#comment21385523)
- [아이디를 알아낸다는 의미가 어떤걸 말씀하시는지 잘 모르겠습니다만 글쓴이를 크롤링 하고싶으신 거라면 copy select로 주소를 따와서 텍스트로 형변환시키면 될것 같습니다.](https://gorokke.tistory.com/20#comment21376012)
- [소중한 정보 잘봤습니다 이런 질문드려도 될지 모르겠지만.. 혹시 아이뒤를 알아내는 방법도 동일한가요? full xpath를 이용해서 해보려고 하는데 잘안되네요ㅠ](https://gorokke.tistory.com/20#comment21375877)
- [제2의 비트코인 꼭보세요!! (이제 올라갈듯 ㅋ) 2008년에 비트코인을 매일 50코인을 무료로 채굴할 수 있었습니다. 대부분의 사람들은 가치가 없다고 느꼈습니다. 지금 비트코인(Bitcoin)은 1코인당 6000만원 상⋯](https://gorokke.tistory.com/181#comment21341756)

## 방문자 통계

93,977

오늘 : 256

어제 : 305

**Java, IntelliJ/Spring**

# JWT토큰이란, 장단점, 구현

고로케 2021. 7. 14.

목차

- [JWT(JSON Web Token) 이란](https://gorokke.tistory.com/181#JWT(JSON_Web_Token)_이란)
- [언제 사용하는가](https://gorokke.tistory.com/181#언제-사용하는가)
- [JWT 구조](https://gorokke.tistory.com/181#jwt-구조)
- [Header/ Payload/ Signature](https://gorokke.tistory.com/181#Header/_Payload/_Signature)
- JWT토큰 장단점
  - [JWT spring 구현](https://gorokke.tistory.com/181#JWT_spring_구현)
- JWT 를 통한 인증 절차





![JWT토큰이란, 장단점, 구현](https://blog.kakaocdn.net/dn/b83546/btq9ynNspjK/M2QYx98gmtBv1as4OGe930/img.png)



#### JWT(JSON Web Token) 이란

> JSON Web Token (JWT) 은 웹표준 (RFC 7519) 으로서 
> 두 개체에서 JSON 객체를 사용하여 가볍고 자가수용적인 (self-contained) 방식으로
>  정보를 안전성 있게 전달해줍니다.

- 자가 수용적 (self-contained)
  JWT 는 필요한 모든 정보를 자체적으로 지니고 있습니다. JWT 시스템에서 발급된 토큰은, 토큰에 대한 기본정보, 전달 할 정보 (로그인시스템에서는 유저 정보를 나타내겠죠?) 그리고 토큰이 검증됐다는것을 증명해주는 signature 를 포함하고있습니다.

 

#### 언제 사용하는가

1. 로그인
   - 사용자 로그인 -> 서버가 해당 유저의 토큰을 유저에게 전달 (JWT)
     -> 유저가 유청을 할때 토큰을 포함해서 전달
     -> 서버는 해당 토큰일 권한이 있는지 유효하고 인증이 되었는지 확인하고 작업을 진행
   - 서버는 유저의 세션을 유지할 필요가 없다.
     유저가 보낸 토큰만 확인하면 된다.
     서버의 자원을 아낄수 있다.
2. 정보교류
   - JWT는 두 개체 사이에서 안정성있게 정보를 교환하기에 좋은 방법이다.
     그 이유는, 정보가 sign 이 되어있기 때문에 정보를 보낸이가 바뀌진 않았는지,
     또 정보가 도중에 조작되지는 않았는지 검증할 수 있다.

#### JWT 구조



![JWT토큰이란, 장단점, 구현 - undefined - undefined - JWT 구조](https://blog.kakaocdn.net/dn/R5BqZ/btq9wgnbnGV/x9paytYSlKksUnDLK0AO10/img.png)



- **Header, Payload, Signature**의 3부분으로 이루어져 있다.
  Json 형태인 각 부분은 **Base64**로 인코딩 되어 표현된다. 각 부분을 이어주기 위해 .구분자를 반환한다.
- Base64는 암호화된 문자열이 아니고, 같은 문자열에 대해 항상 같은 문자열을 반환한다



![JWT토큰이란, 장단점, 구현 - undefined - undefined - JWT 구조](https://blog.kakaocdn.net/dn/bCnPkT/btq9ynF8GpN/NCmsYv3wvGNxQWylRLJti0/img.png)



#### Header/ Payload/ Signature

1. **Header**

- Header 는 두가지의 정보를 지니고 있다.
- typ: 토큰의 타입을 지정. ex)JWT
- alg: 해싱 알고리즘을 지정합니다. 해싱 알고리즘으로는 보통 HMAC SHA256 혹은 RSA 가 사용되며, 이 알고리즘은, 토큰을 검증 할 때 사용되는 signature 부분에서 사용.

```
{ 
 "alg": "HS256",
 "typ": JWT
}
```

 

1. **Payload**

- Payload 부분에는 토큰에 담을 정보가 들어있습니다. 여기에 담는 **정보의 한 ‘조각’ 을 클레임(Claim)** 이라고 부르고, 이는 Json(Key/Value) 형태의 한 쌍으로 이뤄져있습니다. 토큰에는 여러개의 클레임들을 넣을 수 있다.

- 클레임 의 종류는 다음과 같이 크게 세 분류로 나뉘어져있다:

  1) **등록된 (registered) 클레임**
     iss: 토큰 발급자 (issuer)
     sub: 토큰 제목 (subject)
     aud: 토큰 대상자 (audience)
     exp: 토큰의 만료시간 (expiraton),
     시간은 NumericDate 형식으로 되어있어야 하며
     (예: 1480849147370) 언제나 현재 시간보다 이후로 설정되어있어야한다.

  nbf: Not Before 를 의미하며, 토큰의 활성 날짜와 비슷한 개념.
  여기에도 NumericDate 형식으로 날짜를 지정하며,
  이 날짜가 지나기 전까지는 토큰이 처리되지 않는다.
  iat: 토큰이 발급된 시간 (issued at), 이 값을 사용하여 토큰의 age 가 얼마나 되었는지 판단 할 수 있다.
  jti: JWT의 고유 식별자로서, 주로 중복적인 처리를 방지하기 위하여 사용.
    일회용 토큰에 사용하면 유용.

  2. **공개(public)클레임**
     공개 클레임들은 충돌이 방지된 (collision-resistant) 이름을 가지고 있어야 한다.
     충돌을 방지하기 위해서는, 클레임 이름을 URI 형식으로 짖는다.
     등록된 (registered) 클레임
     공개 (public) 클레임
     비공개 (private) 클레임

```
{
   "https://velopert.com/jwt_claims/is_admin": true
}
```


### 3. Signature

- 서명(Signature)은 토큰을 인코딩하거나 유효성 검증을 할 때 사용하는 고유한 암호화 코드
- 서명(Signature)은 위에서 만든 헤더(Header)와 페이로드(Payload)의 값을 각각 BASE64로 인코딩하고, 인코딩한 값을 비밀 키를 이용해 헤더(Header)에서 정의한 알고리즘으로 해싱을 하고, 이 값을 다시 BASE64로 인코딩하여 생성.

-----

### 세션을 대체하지 못하는 이유

JWT는 세션처럼 모든 사용자들의 상태를 기억하고 있지 않다. 따라서 기억하는 대상들의 상태를 언제든 제어할 수 있지 않다. 예를 들어, 세션을 이용한 경우 한 기기에서만 로그인 가능한 서비스를 만들고 싶을 때, pc에서 로그인 하면 핸드폰에서의 세션 값은 사용못하게 하는 등 제어할 수 있다.

반면 JWT는 이미 줘버린 토큰을 뺏을 수 도 없다. 해커에게 토큰을 빼앗겨도 토큰을 무효화할 방법도 없다.

