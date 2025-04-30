# 배열(Array) & 리스트(List)
### 1. 배열 (Array)
## 기본 개념
+ 같은 타입의 데이터 집합을 연속적으로 저장

+ 크기 고정: 선언 시 크기 결정 → 이후 변경 불가

+ 메모리에 연속적으로 저장되므로 접근 속도 빠름

+ 일반적으로 간단한 데이터 집합에 적합
### 선언 방법
```
int[] nums1 = new int[5];                 // 크기만 지정
int[] nums2 = { 1, 2, 3, 4, 5 };          // 값으로 초기화
string[] names = new string[] { "Tom", "Jane", "Lucy" }; // new 사용
```
### 배열 순회
```
// for문
for (int i = 0; i < nums2.Length; i++)
{
    Console.WriteLine(nums2[i]);
}

// foreach문
foreach (var name in names)
{
    Console.WriteLine(name);
}
```
### 주요 기능 및 특징
기능 | 설명 | 예제
|---|---|---|
.Length | 배열의 길이 | nums2.Length → 5
정렬 | Array.Sort(array); 사용 | Array.Sort(nums2);
검색 | Array.IndexOf(array, value); | Array.IndexOf(nums2, 3) → 2
복사 | Array.Copy(src, dest, length); | Array.Copy(nums2, nums1, 3);
다차원 배열 | 2차원 배열, 계단형 배열 지원 | 아래 예시 참고
### 다차원 배열
### + 2차원 배열 (Matrix)
```
int[,] matrix = new int[2, 3] { { 1, 2, 3 }, { 4, 5, 6 } };
Console.WriteLine(matrix[1, 2]); // 6
```
### + 계단형 배열 (Jagged Array)
```
int[][] jagged = new int[2][];
jagged[0] = new int[] { 1, 2 };
jagged[1] = new int[] { 3, 4, 5 };
Console.WriteLine(jagged[1][2]); // 5
```
### 2. 리스트 (List<T>)
## 기본 개념
+ System.Collections.Generic 네임스페이스에 포함

+ 동적 크기 조절: 요소 추가/삭제 가능

+ 제네릭(Generic) 기반 → 타입 안정성 보장

+ 많은 기능과 메서드 제공 → 배열보다 유연
### 선언 및 초기화
```
List<int> scores = new List<int>(); // 빈 리스트
List<string> colors = new List<string> { "red", "blue", "green" };
```
### 리스트 다루기
### + 요소 추가
```
scores.Add(95);
scores.AddRange(new List<int> { 88, 76 });
```
### + 요소 삭제
```
scores.Remove(88);     // 값으로 삭제
scores.RemoveAt(0);    // 인덱스로 삭제
```
### + 검색 & 조건
```
bool exists = scores.Contains(76);           // true/false
int found = scores.Find(x => x > 80);        // 조건에 맞는 첫 요소
List<int> filtered = scores.FindAll(x => x > 80); // 조건에 맞는 전체 리스트
```
### + 순회
```
foreach (var score in scores)
{
    Console.WriteLine(score);
}
```
### 기타 메서드
메서드 | 설명
|---|---|
Insert(index, value) | 특정 위치에 삽입
Clear() | 전체 요소 제거
Count | 현재 요소 수
Sort() | 정렬
Reverse() | 역순 정렬

### 배열 vs 리스트 핵심 비교
항목 | 배열 (Array) | 리스트 (List<T>)
|---|---|---|
크기 | 고정 | 동적
타입 안정성 | 있음 | 있음
성능 | 더 빠름 (단순) | 유연하나 약간 느릴 수 있음
기능 | 기본만 있음 | 다양한 메서드 제공
사용 시점 | 크기가 정해져 있을 때 | 유동적인 데이터 처리할 때

