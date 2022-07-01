# Retrofit vs OkHttp

### 1. OkHttp

- okHttp는 서버와 Http, Http/2 프로토콜 통신을 위한 클라이언트 라이브러리이다.

공식사이트 : https://square.github.io/okhttp/

OkHttp를 사용하지 않고 Http통신하기 위해서는
① HttpUrlConnection으로 연결
② Buffer를 통한 입출력
③ 예외 처리
등의 하나하나 처리해나가야 할 코드가 많은데
okHttp를 사용하면 간단하게 해결.

### 2. Retrofit

- Type-Safe(프로그램 동작이 잘 정의 된 것)한 Http클라이언트 라이브러리이다. Restful통신을 쉽게 할 수 있다.

공식사이트 : https://square.github.io/retrofit/

① OkHttp는 Retrofit의 베이스.

-> 즉, Retrofit안에 OkHttp가 포함되어 있다는 의미랑 비슷.