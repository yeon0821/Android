# SharedPrerfereences

1.SharedPreferences란?

안드로이드 앱 개발을 진행하다 보면, 앱의 데이터들을 저장하여 관리해야 할 상황이 존재한다. 데이터의 양이 많거나 중요 데이터의 경우 서버나 DB에 저장해야겠지만, 간단한 설정 값이나 문자열 같은 데이터를 저장하기 위해 DB를 사용하기는 부담스럽기 때문에 SharedPreferences를 사용하는 것이 적합.

## 2. SharedPreferences의 특징

- 보통 초기 설정값이나 자동 로그인 여부 등 간단한 값을 저장하기 위해 사용
- Application에 파일 형태로 데이터를 저장
- Application이 삭제되기 전까지 저장한 데이터가 보존
- Key-value 방식

------

> MODE의 종류

- MODE_PRIVATE : 생성한 Application에서만 사용 가능
- MODE_WORLD_REDABLE : 외부에서 App에서 사용 가능, But 읽기만 가능
- MODE_WORLD_WRITEABLE : 외부 App에서 사용 가능, 읽기/쓰기 가능

------

## 3. **SharedPreferences 사용 과정**

핵심적인 부분은 다음과 같이 3가지 과정으로 나눌 수 있다.

### **1) 변수 선언 및 초기화**

**변수 선언**

> SharedPreferences pref;
>
> **SharedPreferences.Editor editor;**

**초기화**

> pref = getSharedPreferences("pref", Activity.MODE_PRIVATE);
>
> **editor = pref.edit();**

### **2) 초기값 지정 및 저장값 불러오기**

식별값과 초기값을 직접 지정.

(어떤 이름으로 저장하고 불러올지, 저장값이 없을 때 불러올 값)

> pref.getInt("MyInt01", 0);

### **3) 원하는 값 저장하기**

MyInt01에 10을 저장한다고 가정하면

> editor.putInt("MyInt01", 10);
>
> **editor.apply();**

- editor.apply();를 해야만 저장이 실행