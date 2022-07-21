# ViewBinding?

## 🤷‍♂️ View Binding 이란?

> findViewById 를 쓰지 않고, XML의 view component에 접근하는 object를 반환받아
> view에 접근하는 방식이다.
> 👉🏻 단순히 findViewById를 대체하기 위한 방법으로만 사용된다.

## 💡 장점

1. findViewByid로 없는 id의 view를 찾아오는 경우 null 반환 문제 해결(null-safety)
2. 반환 타입이 일치하지 않을 떄 excepion 발생 문제 해결 (type-safety)
3. 뷰의 개수대로 코드를 추가 할 필요❌

## 👨‍💻 구현

1. build.gradle에서 enable

```groovy
android{
	...
    
    // Android 3.6 ~ 4.0
    viewBinding{
    	enabled = true
    }
    
    // Android 4.0 ~
    buildFeatures{
    	viewBinding = true
    }
}
```

안드로이드 버전에 따라 코드를 추가해준다.
`Sync Now` 를 누르게 되면 모든 layout에 대해서 binding object가 생성된다.
binding object는 id를 갖는 모든 view들을 하나의 property로 가진다.

1. Activity에서 binding 선언

   ```java
   private ActivityMainBinding binding;
   
      @Oerride void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState)
           binding = ActivityMainBinding.inflate(getLayoutInflater());
           setContentView(binding.getroot()); 	
       }
   ```

