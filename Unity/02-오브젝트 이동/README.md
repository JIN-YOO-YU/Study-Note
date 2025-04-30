# 오브젝트 이동 스크립트
1. 목표
유니티에서 키보드 입력을 통해 오브젝트를 움직이는 방법을 이해하고, 실제로 작동하는 스크립트를 작성할 수 있다.

2. 필요한 구성 요소
+ 빈 GameObject 또는 이동시킬 3D 오브젝트 (예: Cube)
+ 스크립트 (C#): 오브젝트 이동 로직을 포함한 컴포넌트
+ Unity Input System: 기본 입력 함수 사용 (기본 설정으로 가능)

3. 기본 이동 스크립트 예제
```
using UnityEngine;
public class PlayerMovement : MonoBehaviour
{
    // 이동 속도를 조절할 수 있는 공개 변수
    public float speed = 5f;

    void Update()
    {
        // 키보드 입력 받기 (수평 및 수직 방향)
        float moveX = Input.GetAxis("Horizontal"); // A, D 키 또는 ←, →
        float moveZ = Input.GetAxis("Vertical");   // W, S 키 또는 ↑, ↓

        // 방향 벡터 생성
        Vector3 movement = new Vector3(moveX, 0, moveZ);

        // 이동 거리 계산 (프레임 보정 포함)
        transform.Translate(movement * speed * Time.deltaTime);
    }
}
```
4. 코드 설명

| 코드 라인 | 설명 |
|---|---|
| `public float speed = 5f;` | 오브젝트의 이동 속도를 조절할 수 있는 변수입니다. 에디터에서 직접 조정 가능 |
| `Input.GetAxis("Horizontal")` | 좌우 방향 키 입력을 받아 -1.0 ~ 1.0 범위의 값을 반환합니다 (A: -1, D: +1) |
| `Input.GetAxis("Vertical")` | 상하 방향 키 입력을 받아 -1.0 ~ 1.0 범위의 값을 반환합니다 (S: -1, W: +1) |
| `Vector3 movement = new Vector3(moveX, 0, moveZ);` | 입력값을 바탕으로 이동 방향을 정의 (Y축은 사용하지 않음) |
| `transform.Translate(...)` | GameObject를 지정한 방향으로 이동시킵니다 |
| `Time.deltaTime` | 프레임 간 시간 차를 곱해 **일정한 속도**를 유지하게 합니다 (프레임 속도에 따라 움직임 변화 방지) |
5. 사용 방법
> 1.3D Object > Cube 등으로 이동할 오브젝트를 생성합니다.
> 
> 2.PlayerMovement.cs라는 이름으로 새 스크립트를 생성하고 위 코드를 붙여넣습니다.
> 
> 3.Cube에 스크립트를 드래그해 추가하거나, Add Component 버튼으로 추가합니다.
> 
> 4.Speed 값을 조절해서 이동 속도를 테스트합니다.
> 
> 5.Play 버튼을 눌러 방향키(WASD 또는 방향키)로 이동을 확인합니다.
