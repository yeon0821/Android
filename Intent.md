# Intent

안드로이드에서는 화면간 이동과 화면간 데이터 전달이 무척이나 빈번하고 중요.  안드로이드에서 페이지 전환과 페이지 간 데이터 전달은 intent를 통해 구현 가능.

- 인텐트란

인텐트는 앱 컴포넌트가 무엇을 할 것인지를 담는 메시지 객체.  메시지는 의사소통을 하기 위해 보내고 받는 것. 베시지를 사용하는 가장 큰 목적은 다른 액티비티, 서비스, 브로드캐스트 리시버, 프로바이더 등을 실행하는 것이다. 인텐트는 그들 사이에 더이터를 주고 받기 위한 용도로 쓰인다.

- intent의 통신 방법은 두가지(명시적, 암시적) 방법이 있다.

1. 명시적 intent
2. 암시적 intent

------

## 1. 명시적 인텐트

- 명시적 인텐트는 가장 많이 볼 수 있는 방법.  앱의 화면전환을 하는 방법

하나의 액티비티에서 다른 액티비티로의 화면 전환시 사용하는 것.

## 1- 1 화면 이동 간 예제

```java
Intent intent = new Intent(A_Activity.this, B_Activity.class);
startActivity(intent);
```

현재 액티비티(A_Activity) 에서 다른 액티비티(B_Activity)를 호출할 때 사용.

B_Activity.class 생성시 AndroidManifest.xml에도 액티비티를 사용하겠다고 정의를 해야 한다.

<activity android:name=".B_Activity">

인텐트는 액티비티 호출시 데이터를 전달 또는 데이터를 리턴 받을 수 있습니다.

- A_Activity에서 B_Activity에 데이터 전달하고 B_Activity 종료시 리턴값을 받을 때

A_Activity - startActivityForResult() 메소드로 B_Activity를 호출하고 onActivityResult()로 리턴값을 받습니다.

```java
Intent intent = new Intent(A_Activity.this, B_Activity.class);
startActivityForResult(intent, 100);
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    switch (requestCode){
        case 100:
            if(data.getExtras() != null){
                String str = data.getStringExtra("resultKey");
                result01.setText("startAcitivtyForResult() 리턴값 받기: " + str);
            }
            break;
    }
    super.onActivityResult(requestCode, resultCode, data);
}
```

------

## 2. 암시적 인텐트

- 암시적 인텐트는 intent의 Action에 따라 해당하는 적합한 애플리케이션의 클래스를 호출. 이 때 단하나가 아닌 여러개가 호출 될 수 있다.
- 암시적 인텐트는 웹 브라우저 호출, 이메일 전송, 전화 앱으로의 통화 등 해당.

웹브라우저 인텐트 호출

```java
Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("<http://m.naver.com>"));
startActivity(intent);
```

이메일 전달 인텐트 호출

```java
Intent intent = new Intent(Intent.ACTION_SEND);
intent.setType("text/plain");
intent.putExtra(Intent.EXTRA_EMAIL, "sampleXXX@sampleXXX.com");
intent.putExtra(Intent.EXTRA_SUBJECT, "전달할 이메일 제목");
intent.putExtra(Intent.EXTRA_TEXT, "전달할 내용");
startActivity(Intent.createChooser(intent, "Choose Email"));
```

전화걸기 인텐트 호출

```java
Intent intent = new Intent(Intent.ACTION_VIEW,Uri.parse("tel:010-0000-0000"));
startActivity(intent);
```

- A_Activity.java

```java
package com.studio572.sampleintent;

import android.content.Intent;
import android.net.Uri;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class A_Activity extends AppCompatActivity {

    Button button01, button02, button03, button04, button06;
    TextView result01;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        button01 = (Button) findViewById(R.id.button01);
        button02 = (Button) findViewById(R.id.button02);
        button03 = (Button) findViewById(R.id.button03);
        button04 = (Button) findViewById(R.id.button04);
        button06 = (Button) findViewById(R.id.button06);
        result01 = (TextView) findViewById(R.id.result01);

        button01.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(A_Activity.this, B_Activity.class);
                startActivity(intent);
            }
        });
        button02.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(A_Activity.this, B_Activity.class);
                // 데이터 전달
                intent.putExtra("key", "데이터가 전달 되었습니다.");
                startActivity(intent);
            }
        });
        button03.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(A_Activity.this, B_Activity.class);
                startActivityForResult(intent, 100);
            }

        });

        button04.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("<http://m.naver.com>"));
                startActivity(intent);
            }
        });

        button06.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(Intent.ACTION_VIEW,Uri.parse("tel:010-0000-0000"));
                startActivity(intent);
            }
        });
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        switch (requestCode){
            case 100:
                if(data.getExtras() != null){
                    String str = data.getStringExtra("resultKey");
                    result01.setText("startAcitivtyForResult() 리턴값 받기: " + str);
                }
                break;
        }
        super.onActivityResult(requestCode, resultCode, data);
    }
}
```

- activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="<http://schemas.android.com/apk/res/android>"
    xmlns:app="<http://schemas.android.com/apk/res-auto>"
    xmlns:tools="<http://schemas.android.com/tools>"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.studio572.sampleintent.A_Activity">

    <Button
        android:id="@+id/button01"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Intent 실행"/>
    <Button
        android:id="@+id/button02"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Intent data 전달"/>
    <Button
        android:id="@+id/button03"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Intent startActivityForResult()"/>

    <TextView
        android:id="@+id/result01"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:gravity="center"
        android:text="startAcitivtyForResult() 리턴값 받기"/>

    <Button
        android:id="@+id/button04"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="웹브라우저 실행"/>

    <Button
        android:id="@+id/button06"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="전화걸기 실행"/>

</LinearLayout>
```

- B_Activity.java

```java
package com.studio572.sampleintent;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.support.annotation.Nullable;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

/**
 * Created by Administrator on 2017-08-13.
 */

public class B_Activity extends Activity{

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main02);

        TextView textView = (TextView) findViewById(R.id.text01);
        Button result01 = (Button) findViewById(R.id.result01);
        Button result02 = (Button) findViewById(R.id.result02);

        Intent getIntent = getIntent();

        if(getIntent.getExtras() != null){
            String str = getIntent.getStringExtra("key");
            textView.setText(str);
        }

        result01.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                finish();
            }
        });
        result02.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent resultIntent = new Intent();
                resultIntent.putExtra("resultKey", "리턴값 받음");
                setResult(RESULT_OK,resultIntent);
                finish();
            }
        });
    }
}
```

- activity_main02.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout  xmlns:android="<http://schemas.android.com/apk/res/android>"
    xmlns:app="<http://schemas.android.com/apk/res-auto>"
    xmlns:tools="<http://schemas.android.com/tools>"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <TextView
        android:id="@+id/text01"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:text="데이터 전달 받은 것이 없습니다."
        android:gravity="center"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/result01"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Acitivty 종료"/>
    <Button
        android:id="@+id/result02"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Activity result값 주면서 종료"/>
</LinearLayout>
```

- AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="<http://schemas.android.com/apk/res/android>"
    package="com.studio572.sampleintent">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".A_Activity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity android:name=".B_Activity"/>
    </application>

</manifest>
```