# Spinner
1. Spinner 개요
+ Spinner는 드롭다운 형식으로 데이터를 선택할 수 있게 해주는 UI 컴포넌트

+ EditText처럼 사용자 입력을 받는 것이 아니라, 제공된 리스트에서 선택하는 구조

+ 기본적으로 ArrayAdapter를 통해 데이터를 설정하며, 필요에 따라 커스텀 뷰로 확장 가능


2. 기본 구현 흐름
2-1.XML에서 Spinner 뷰 정의

2-2.코드에서 Spinner 뷰 참조

2-3.Adapter를 생성하여 Spinner에 설정

2-4.선택 이벤트 처리

3.XML 레이아웃
```
<!-- activity_main.xml -->
<Spinner
    android:id="@+id/spinner_example"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:spinnerMode="dropdown"  <!-- or "dialog" -->
    android:prompt="@string/spinner_prompt" />
```
4.strings.xml: 항목 배열 정의
```
<!-- res/values/strings.xml -->
<string-array name="fruit_array">
    <item>사과</item>
    <item>바나나</item>
    <item>포도</item>
    <item>복숭아</item>
</string-array>
```
5.MainActivity.java: Spinner 연결
```
public class MainActivity extends AppCompatActivity {

    Spinner spinner;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        spinner = findViewById(R.id.spinner_example);

        ArrayAdapter<CharSequence> adapter = ArrayAdapter.createFromResource(
            this,
            R.array.fruit_array,
            android.R.layout.simple_spinner_item
        );

        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
        spinner.setAdapter(adapter);

        spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {
                String selected = parent.getItemAtPosition(position).toString();
                Toast.makeText(MainActivity.this, selected + " 선택됨", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onNothingSelected(AdapterView<?> parent) {
                // 선택되지 않은 경우
            }
        });
    }
}
```
6.동적 데이터 Spinner (ArrayList 사용)
```
ArrayList<String> colors = new ArrayList<>();
colors.add("빨강");
colors.add("파랑");
colors.add("노랑");

ArrayAdapter<String> adapter = new ArrayAdapter<>(
    this,
    android.R.layout.simple_spinner_item,
    colors
);
adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
spinner.setAdapter(adapter);
```
7.커스텀 Spinner (뷰 커스터마이징)
```
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/text"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="8dp"
    android:textSize="16sp"
    android:textColor="#000000" />
```
7.커스텀 Spinner (뷰 커스터마이징)
```
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/text"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="8dp"
    android:textSize="16sp"
    android:textColor="#000000" />
```
8.어댑터에서 커스텀 레이아웃 적용
```
ArrayAdapter<String> customAdapter = new ArrayAdapter<>(
    this,
    R.layout.spinner_item,
    colors
);
customAdapter.setDropDownViewResource(R.layout.spinner_item);
spinner.setAdapter(customAdapter);
```
