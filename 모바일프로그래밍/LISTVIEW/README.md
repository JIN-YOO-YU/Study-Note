# LISTVIEW 실습
```
package com.example.myapplication;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.Button;
import android.widget.ListView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity
        implements View.OnClickListener, AdapterView.OnItemClickListener {//

    private String[] list_items = {"item01","item02","item03","item04","item05","item06","item07","item08","item09","item10",
            "item11","item12","item13","item14","item15"};
    Button btn01;
    ListView lv;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
        btn01 = (Button) findViewById(R.id.button01);
        btn01.setOnClickListener(this);

        lv = (ListView) findViewById(R.id.list01);

        ArrayAdapter<String> adapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, list_items);
        lv.setAdapter(adapter);
        lv.setOnItemClickListener(this);

    }

    @Override
    public void onClick(View v) {
        finish();
    }

    @Override
    public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {
        Toast.makeText(this, "Click item = " + list_items[i], Toast.LENGTH_LONG ).show();
    }
}
```
+ 클래스 선언

  ```
public class MainActivity extends AppCompatActivity 
        implements View.OnClickListener, AdapterView.OnItemClickListener {
```


> + public: 이 클래스가 공개되어 있음(public)을 의미
> + class MainActivity: MainActivity라는 이름의 클래스를 정의하고 안드로이드에서는 하나의 화면을 하나의 클래스로 표현하는 것이 일반적이므로 이 MainActivity는 앱의 첫 번째 화면을 담당
> + extends: extends는 상속을 의미 즉 MainActivity는 AppCompatActivity의 기능을 상속받아 사용
> + AppCompatActivity: 안드로이드에서 기본 액티비티 기능을 제공하는 클래스로 UI 표시, 생명주기 관리, 버튼 클릭, 화면 전환 등 다양한 기능을 사용할 수 있게 해줌
> + implements: implements는 해당 클래스가 특정 인터페이스를 구현 한다는 뜻
> + View.OnClickListener: 버튼 같은 뷰가 클릭될 때 어떤 동작을 할지 정의할 수 있는 인터페이스
이걸 구현했다는 건 이 클래스 안에 다음과 같은 메서드가 있어야 한다는 걸 의미
```
@Override
public void onClick(View v) {
    // 버튼 클릭 시 실행될 코드
}
```
