# Retrofit이란?


## Retrofit2 - REST API 통신 라이브러리

'Retrofit' - REST통신 라이브러리 기본 개념 & 사용법

통신 라이브러리** 중 가장 많이 사용되는 **대표적인** 라이브러리 ( Squareup 사의 라이브러리)





## **Retrofit 이란?**

- REST API 통신을 위해 구현된 

- 동일 Squareup사의 **OkHttp 라이브러리의 상위 구현체**

   : **Retrofit**은 OkHttp를 네트워크 계층으로 활용하고 그 위에 구축됨

- **AsyncTask 없이 Background Thread 실행 -> Callback을 통해 Main Thread에서 UI 업데이트**

  



![img](https://blog.kakaocdn.net/dn/l8qRO/btqCZx129QA/fipgu9Qwv1EvHobxQOlH2K/img.png)

## **Retrofit 장점 / 단점**

- **빠른 성능**
     Okhttp는 AsyncTask를 사용 (AsyncTask의 3~10배의 성능차이가 난다고 함)

- **간단한 구현** - 반복된 작업을 라이브러리 넘겨서 처리
    HttpUrlConection의 Connection / Input&OutputStream / URL Encoding 생성 및 할당의 반복작업

    OkHttp의 쿼리스트링, Request / Response 반복 설정 작업  

- **가독성**
    Annotation(애노테이션) 사용으로 코드의 가독성이 뛰어남, 직관적인 설계가 가능

- **동기/비동기 쉬운 구현
  **  **동기 Synchronous** - 동시에 일어난다는 의미로, 요청-응답이 하나의 트랜잭션(작업)에서 발생
                 요청 후 응답까지 대기한다는 의미

    **비동기 Asynchronous** - 동시에 일어나지 않는다는 뜻으로, 요청-응답은 별개의 트랜잭션
                    요청 후 응답이 도착하면 Callback으로 받아서 처

  



## **3가지 구성요소**

- **DTO (POJO)** - 'Data Transfer Object', 'Plain Old Java Object' 형태의 모델(Model) / JSON 타입변환에 사용
- **Interface** - 사용할 HTTP CRUD동작(메소드) 들을 정의해놓은 인터페이스
     \* **CRUD** ( Create / Read / Update / Delete ) -> **HTTP Method** ( POST / GET / PUT / DELETE )
- **Retrofit.Builder 클래스** - Interface를 사용할 인스턴스, baseUrl(URL) / Converter(변환기) 설정

 



## **사용방법**

**REST API 테스트 사이트인 -> JsonPlaceHolder 예시로 실행**

**요청할 URL** -> https://jsonplaceholder.typicode.com/posts/1



![img](https://blog.kakaocdn.net/dn/437vt/btqCZZD0qkB/ersZ9cJf0X84XiLKm7uT00/img.jpg)REST API 응답 데이터



### **1. Gradle 의존성 추가**

- Retrofit / Converter (변환기) 라이브러리 추가

```
// Retrofit 라이브러리
implementation 'com.squareup.retrofit2:retrofit:2.6.4' 

// Gson 변환기 라이브러리
implementation 'com.squareup.retrofit2:converter-gson:2.6.4'    

// Scalars 변환기 라이브러리
implementation 'com.squareup.retrofit2:converter-scalars:2.6.4' 
```

- **Gson Converter** - JSON 타입의 응답결과를 객체로 매핑(변환)해주는 Converter
- **Scalars Converter** - 응답결과를 String자체로 받아서 보여주는 Converter (사용자가 직접 변환시 사용)
- 그 외에 Moshi / Jackson 등등 여러 컨버터가 존재

 



**1-1. 인터넷 권한 설정 'Permission-INTERNET'**

- 메니페스트(Manifests) 파일에 인터넷 권한(퍼미션) 추가 - 네트워크 통신에 필요 
- **<uses-permission android:name="android.permission.INTERNET"/>**



![img](https://blog.kakaocdn.net/dn/cfVuUd/btqC21uzRJr/7kiraAWCStSAlGLXKUTwKK/img.png)Permission 추가





 

 



### **2. DTO / POJO - 모델 클래스 생성**

- **REST API로 받아올 데이터**를 변환하여 매핑할 **DTO 클래스 선언**
- **REST API의 응답 데이터 구조에 맞게 모델 클래스 선언 - 클래스명은 상관x**

```
// REST API 응답데이터 구조

{
	"userId": 1,
	"id": 1,
	"title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
	"body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

// DTO 모델 - PostResult Class 선언
public class PostResult {
    
    @SerializedName("userId")
    private int userId;
    
    @SerializedName("id")
    private int id;
    // @SerializedName으로 일치시켜 주지않을 경우엔 클래스 변수명이 일치해야함
    
    private String title;
    // @SerializedName()로 변수명을 입치시켜주면 클래스 변수명이 달라도 알아서 매핑시켜줌  
    
    @SerializedName("body")
    private String bodyValue;

    // toString()을 Override 해주지 않으면 객체 주소값을 출력함
    @Override
    public String toString() {
        return "PostResult{" +
                "userId=" + userId +
                ", id=" + id +
                ", title='" + title + '\'' +
                ", bodyValue='" + bodyValue + '\'' +
                '}';
    }
}
```

 

- **JSON 데이터의 속성명과 변수명 + 타입(ex String,Int,Boolean) 일치 필수
     : JSON - @SerializedName("속성명")으로 속성명 일치시켜주면 변수명 다르게도 가능
   
  **    **XML - @Element(name="속성명") XML은 @Element 애노테이션 사용**

 

 



## **Interface 정의**

- **사용할 메소드 선언**

```
public interface RetrofitService {

	// @GET( EndPoint-자원위치(URI) )
   	@GET("posts/{post}")
 	Call<PostResult> getPosts(@Path("post") String post);
   	 
}
```

 



![img](https://blog.kakaocdn.net/dn/c2OmS5/btqC22GtD3X/ovmY3HFoXb5FbrEzweIZv1/img.png)



- **@GET("posts/{post}")** - 요청메소드 GET, baseUrl에 연결될 EndPoint 'posts/{post} 
- **반환타입 Call<PostResult>** - Call은 응답이 왔을때 Callback으로 불려질 타입
    **PostResult** - 요청GET에 대한 응답데이터를 받아서 DTO 객체화할 클래스 타입 지정 
- **메소드명 "getPosts"** - 자유롭게 설정, 통신에 영향 x
- **매개변수 '@Path("post") String post'** - 매개변수 post가 @Path("post")를 보고 @GET 내부 {post}에 대입

 

 







## **Retrofit 인스턴스 생성**

- **Retrofit.Build를 통해 Retrofit 인스턴스 생성**
   \- baseUrl, Converter, Client 설정 부분 (baseUrl는 꼭 / 로 끝나야 함, 아니면 예외 발생)
   \- **Converter**는 여러개 등록 가능, 등록 순서대로 변환 가능여부 판단, 변환 불가능하면 다음 컨버터 확인    **GsonConverter**를 **마지막**에 넣는걸 추천 **(Gson은 변환이 불가능해도 가능하다고 반응함)**
- **Interface 객체 구현**
     \- retrofit을 통한 객체 구현, 추상 메소드 중 사용할 메소드 Call 객체에 등록
- **동기 / 비동기 통신작업 실행 
  **   - 비동기 enqueue 작업으로 실행, **통신종료 후 이벤트 처리를 위해 Callback 등록
  **   - **onResponse 성공 / onFailure 실패** 구분하여 **메인스레드**에서 처리할 작업 등록
      (onResponse가 무조건 성공 X, 실패코드(3xx & 4xx 등)에도 호출 - **isSuccesful() 확인이 필요**



![img](https://blog.kakaocdn.net/dn/A65n0/btqCZyzOPXi/9qudu2jQ9PiP6vTkzkYOfk/img.png)



 



**응답 결과**

- 정상적인 응답받아 -> **PostResult 객체 변환 성공**



![img](https://blog.kakaocdn.net/dn/qbj7X/btqCX89vnZl/qVQeMWIL3kkgAwYEKvVvZ1/img.png)정상적인 변환 성공
