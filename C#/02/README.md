<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>C# 반복문 학습노트</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            line-height: 1.6;
            background-color: #f9f9f9;
            padding: 30px;
            color: #333;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        code {
            background-color: #eee;
            padding: 2px 5px;
            border-radius: 4px;
        }
        pre {
            background-color: #f0f0f0;
            padding: 15px;
            border-radius: 5px;
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 15px 0;
        }
        th, td {
            border: 1px solid #ccc;
            padding: 10px;
        }
        th {
            background-color: #e8f0fe;
        }
        ul {
            list-style-type: square;
            margin-left: 20px;
        }
    </style>
</head>
<body>

    <h1>📘 C# 반복문 학습노트</h1>

    <h2>🔍 반복문이란?</h2>
    <p>동일한 코드를 여러 번 실행하고 싶을 때 사용하는 문법입니다. 조건이 맞는 동안 계속 반복됩니다.</p>

    <h2>💡 반복문의 종류</h2>
    <table>
        <tr>
            <th>반복문 종류</th>
            <th>사용 시점</th>
        </tr>
        <tr>
            <td><code>for</code></td>
            <td>반복 횟수가 정해졌을 때</td>
        </tr>
        <tr>
            <td><code>foreach</code></td>
            <td>배열, 리스트 등 컬렉션 순회할 때</td>
        </tr>
        <tr>
            <td><code>while</code></td>
            <td>조건이 참일 동안 반복</td>
        </tr>
        <tr>
            <td><code>do-while</code></td>
            <td>무조건 1번 실행 후 조건 검사</td>
        </tr>
    </table>

    <h2>1️⃣ for 문</h2>
    <h3>📦 기본 구조</h3>
    <pre><code>for (초기화식; 조건식; 증감식)
{
    // 반복 실행될 코드
}</code></pre>

    <h3>🧠 구성요소 설명</h3>
    <table>
        <tr><th>구성</th><th>예시</th><th>설명</th></tr>
        <tr><td>초기화식</td><td><code>int i = 0</code></td><td>반복 변수 선언 및 초기값</td></tr>
        <tr><td>조건식</td><td><code>i &lt; 10</code></td><td>반복 계속할 조건</td></tr>
        <tr><td>증감식</td><td><code>i++</code></td><td>반복할 때마다 값 증가</td></tr>
    </table>

    <h3>🧪 예제</h3>
    <pre><code>for (int i = 1; i <= 5; i++)
{
    Console.WriteLine(i);
}</code></pre>

    <h2>2️⃣ foreach 문</h2>
    <p>배열이나 리스트 같은 컬렉션을 순회할 때 사용합니다.</p>
    <pre><code>string[] names = { "철수", "영희", "민수" };

foreach (string name in names)
{
    Console.WriteLine(name);
}</code></pre>

    <h2>3️⃣ while 문</h2>
    <p>조건이 참이면 반복 실행됩니다. 조건을 먼저 검사합니다.</p>
    <pre><code>int i = 1;
while (i <= 5)
{
    Console.WriteLine(i);
    i++;
}</code></pre>

    <h2>4️⃣ do-while 문</h2>
    <p>최소 1번 실행한 후 조건을 검사합니다.</p>
    <pre><code>string input;

do
{
    Console.Write("계속할까요? (y/n): ");
    input = Console.ReadLine();
} while (input != "n");</code></pre>

    <h2>✅ 반복 제어 키워드</h2>
    <h3>🔹 break</h3>
    <p>반복문을 강제로 중단합니다.</p>
    <pre><code>for (int i = 1; i <= 10; i++)
{
    if (i == 5) break;
    Console.WriteLine(i);
}</code></pre>

    <h3>🔹 continue</h3>
    <p>이번 반복만 건너뛰고 다음 반복으로 넘어갑니다.</p>
    <pre><code>for (int i = 1; i <= 5; i++)
{
    if (i == 3) continue;
    Console.WriteLine(i);
}</code></pre>

    <h2>📊 반복문 선택 가이드</h2>
    <table>
        <tr><th>상황</th><th>추천 반복문</th><th>이유</th></tr>
        <tr><td>정해진 횟수 반복</td><td><code>for</code></td><td>가장 직관적</td></tr>
        <tr><td>배열/리스트 순회</td><td><code>foreach</code></td><td>코드 간결함</td></tr>
        <tr><td>조건만 존재</td><td><code>while</code></td><td>유연한 조건 처리</td></tr>
        <tr><td>최소 1회 실행</td><td><code>do-while</code></td><td>입력/초기 실행용</td></tr>
    </table>

    <h2>✍️ 연습 문제</h2>
    <ul>
        <li>1~100 중 3의 배수만 출력 (<code>for</code>)</li>
        <li>문자열 배열을 <code>foreach</code>로 출력</li>
        <li>숫자 10부터 1까지 출력 (<code>while</code>)</li>
        <li>사용자 입력 받아 "exit" 입력 전까지 반복 (<code>do-while</code>)</li>
        <li>1~10 중 5에서 <code>break</code>, 3은 <code>continue</code></li>
    </ul>

</body>
</html>
