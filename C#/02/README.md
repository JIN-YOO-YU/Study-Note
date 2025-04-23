## C# 반복문 학습노트

+ ### 반복문이란?
+ 동일한 코드를 여러 번 실행하고 싶을 때 사용하는 문법
+ 코드 반복을 줄여서 효율적으로 프로그래밍 가능
+ 조건이 맞는 동안 계속 실행됨

### 1. for 문
+ 구조
```
for (초기화식; 조건식; 증감식)
{
    // 반복 실행될 코드
}
```
구성 | 예시 | 설명
|---|---|---|
초기화식 | int i = 0 | 반복 변수 선언 및 초기값 설정
조건식 | i < 10 | 반복을 계속할 조건
증감식 | i++ | 매 반복마다 변수 변화

+ ### 예제 1: 1~5까지 출력
```
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine(i);
}
```
+ ### 예제 2: 짝수 출력 (1~10)
```
for (int i = 1; i <= 10; i++)
{
    if (i % 2 == 0)
        Console.WriteLine(i);
}
```
```
2
4
6
8
10
```
### 2. foreach 문
+ 배열이나 리스트 같은 컬렉션을 순서대로 순회할 때 사용

+ 구조
```
foreach (데이터타입 변수 in 컬렉션)
{
    // 반복 실행할 코드
}
```
### + 예제: 문자열 배열 출력
```
string[] names = { "철수", "영희", "민수" };

foreach (string name in names)
{
    Console.WriteLine(name);
}
```
```
철수
영희
민수
```
✅ foreach는 읽기 전용. 값을 수정할 수는 없음
❌ 인덱스(i)가 필요할 땐 for문이 더 적합
### 3. while 문
+ 조건이 참일 동안 반복
+ 조건을 먼저 검사함
+ 구조
```
while (조건식)
{
    // 반복 실행할 코드
}
```
### 예제: 1~5까지 출력
```
int i = 1;
while (i <= 5)
{
    Console.WriteLine(i);
    i++;
}
```
```
1
2
3
4
5
```
❗ i++를 빼먹으면 무한 루프 발생 주의!
### 4. do-while 문
+ 먼저 한 번 실행하고, 나중에 조건 검사
```
string input;

do
{
    Console.Write("계속할까요? (y/n): ");
    input = Console.ReadLine();
} while (input != "n");
```
📌 사용자 입력 등을 받을 때 유용
✅ 최소 1회는 무조건 실행됨
### + 반복 제어 키워드
+ break
반복문 강제 종료
```
for (int i = 1; i <= 10; i++)
{
    if (i == 5) break;
    Console.WriteLine(i);
}
```
📌 출력: 1, 2, 3, 4
+ continue
이번 반복만 건너뛰고, 다음 반복으로 이동
```
for (int i = 1; i <= 5; i++)
{
    if (i == 3) continue;
    Console.WriteLine(i);
}
```
출력: 1, 2, 4, 5
