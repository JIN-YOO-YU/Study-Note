# 예외처리

### 예외란?
+ **예외(Exception)**는 프로그램 실행 도중 발생하는 예상치 못한 오류 상황

예: 0으로 나누기, 존재하지 않는 파일 열기, 잘못된 입력 값 등
✔️ 예외를 처리하지 않으면 프로그램은 강제 종료됨

### 예외처리란?
+ 예외 발생 시 프로그램이 멈추지 않도록 안전하게 처리하는 방법
+ try, catch, finally, throw 등의 키워드를 사용
+ ### 주요 키워드 정리
키워드 | 설명
---|---
try | 예외 발생 가능성이 있는 코드를 묶음
catch | 예외가 발생했을 때 실행할 코드
finally | 예외 발생 여부와 관계없이 항상 실행되는 코드
throw | 개발자가 직접 예외를 발생시킬 때 사용


### + 자주 발생하는 예외 종류
예외 이름 | 의미
---|---
DivideByZeroException | 0으로 나누려 할 때
FormatException | 형식이 잘못된 데이터를 변환할 때
OverflowException | 숫자가 자료형 범위를 벗어날 때
IndexOutOfRangeException | 배열, 리스트의 범위를 벗어날 때
NullReferenceException | null 값을 참조하려 할 때
ArgumentException | 잘못된 인자가 전달될 때

### 예외처리 작성 시 주의할 점
+ 너무 넓은 범위의 try문 사용 X → 예외 위치 파악 어려움

+ 가능한 구체적인 예외 타입부터 처리

+catch (Exception)은 가장 마지막에

+ finally는 자원 해제나 종료 메시지 등에 활용

+ 예외 메시지는 사용자 친화적으로 제공

```
//변수 선언 및 입력 받기
int num1 = 10;
int num2 = 0;
int num3, sum;
string str;
//사용자로부터 문자열을 입력받음
Console.Write("키보드 값을 입력해주세요 : ");
str = Console.ReadLine();

try
{
    num2 = int.Parse(str);//문자열을 정수로 변환
    Console.WriteLine(num2);
    num3 = Convert.ToInt32(str);//문자열을 정수로 변환
    Console.WriteLine(num3);
    sum = num1 / num2;//num2 == 0이면 DivideByZeroException 발생
    num2 = int.Parse(str);
//0을 나누는 것과 별개로, 직접 예외 발생시킴
    if (num2 == 0)
        throw new AggregateException("입력이 0 이다");//AggregateException: 보통 여러 예외를 모아서 처리할 때 쓰지만, 여기선 그냥 "사용자 정의 예외 메시지용"

}
catch (AggregateException e)//위에서 throw new AggregateException(...) 했을 때 여기로 감
{
    Console.WriteLine(e.Message);
}

catch (OverflowException e)//너무 큰 숫자 입력으로 오버플로우 발생 시
{
    Console.WriteLine("에러2");
    Console.WriteLine(e.Message);
}

catch (DivideByZeroException e)//0으로 나눌 때 발생
{
    Console.WriteLine("Division of {0} by zero.", num2);
    Console.WriteLine(e.Message);
}
catch (Exception e)//위에서 잡지 못한 모든 예외를 처리하는 일반 예외 블록
{ Console.WriteLine(e.Message); }

catch//예외 정보 없이 마지막 보루로 실행됨
{
    Console.WriteLine("에러1");
}
finally//예외 발생 여부와 상관없이 항상 실행
{
    Console.WriteLine("난 무조건이야");
}
```
