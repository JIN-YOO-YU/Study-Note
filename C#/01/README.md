# C# 기본 개념 핵심 요약

### 1. 변수 (Variable)
+ 값을 저장하는 공간!
```
int age = 25;         // 정수
string name = "홍길동"; // 문자열
double pi = 3.14;     // 실수
bool isTrue = true;   // true or false
```
### 2. 연산자
수학 계산, 비교 등
```
int result = 10 + 5;    // 덧셈
bool check = 10 > 5;    // 비교
```
### 3. 조건문 (if, else)
```
int score = 85;

if (score >= 90)
    Console.WriteLine("A학점");
else if (score >= 80)
    Console.WriteLine("B학점");
else
    Console.WriteLine("C학점");
```
### 4. 반복문 (for, while)
```
for (int i = 1; i <= 5; i++)
{
    Console.WriteLine(i);
}
```
### 5. 배열 (Array)
```
int[] numbers = { 10, 20, 30 };
Console.WriteLine(numbers[0]); // 10
```
### 6. 함수 (Method)
```
void SayHello()
{
    Console.WriteLine("안녕하세요!");
}
SayHello();  // 함수 호출
```
### 7. 클래스와 객체 (Class, Object)
C#은 객체지향 언어 — 모든 게 클래스 기반
```
class Person
{
    public string name;

    public void SayName()
    {
        Console.WriteLine("내 이름은 " + name);
    }
}

// 객체 만들기
Person p = new Person();
p.name = "철수";
p.SayName();
```
### 8. 예외 처리 (try-catch)
```
try
{
    int x = 10 / 0;
}
catch (DivideByZeroException e)
{
    Console.WriteLine("0으로 나눌 수 없습니다.");
}
```
### 기본 구조
+ C# 프로그램은 항상 이런 구조로 시작:
```
using System;

class Program
{
    static void Main(string[] args)
    {
        // 여기에 코드 작성!
        Console.WriteLine("Hello, C#!");
    }
}
```
