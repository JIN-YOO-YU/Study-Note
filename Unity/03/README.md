# 오브젝트 점프 구현
1. 목표
키보드 입력(예: Spacebar)을 받아서 오브젝트가 한 번만 점프하도록 만들고, 바닥에 닿았을 때만 다시 점프 가능하게 구현한다.

2. 준비사항
+ 이동 가능한 3D 오브젝트 (예: Capsule)
+ Rigidbody 컴포넌트가 추가되어 있어야 함 (물리 적용)
+ 바닥 역할을 할 Plane 같은 오브젝트 (Layer 설정 가능)
+ 새 C# 스크립트: PlayerJump.cs

3. 점프 스크립트 예제
```
using UnityEngine;

public class PlayerJump : MonoBehaviour
{
    public float jumpForce = 5f;
    private Rigidbody rb;
    private bool isGrounded = true;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        // 스페이스 키를 누르고 땅에 있을 때만 점프
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded)
        {
            rb.AddForce(Vector3.up * jumpForce, ForceMode.Impulse);
            isGrounded = false;
        }
    }

    // 바닥에 닿으면 다시 점프 가능하게 설정
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
        {
            isGrounded = true;
        }
    }
}
```
4. 코드 설명

| 코드 라인 | 설명 |
|---|---|
| `public float jumpForce = 5f;` | 점프의 힘을 조절할 수 있는 변수 |
| `Rigidbody rb;` | 물리 엔진을 제어하기 위해 Rigidbody 사용 |
| `Input.GetKeyDown(KeyCode.Space)` | 스페이스 키를 한 번 눌렀을 때만 동작 |
| `rb.AddForce(Vector3.up * jumpForce, ForceMode.Impulse);` | 위 방향으로 순간적인 힘을 가해서 점프 |
| `isGrounded` | 점프 중복 방지를 위한 플래그 |
| `OnCollisionEnter()` | 바닥에 닿았는지를 감지하는 충돌 처리 함수 |
| `CompareTag("Ground")` | 바닥 오브젝트는 반드시 “Ground” 태그로 설정해야 작동 |
5. 설정 방법
> 1.Plane 또는 바닥 역할을 할 오브젝트를 생성하고, **태그를 "Ground"**로 설정합니다.

> 2.점프할 오브젝트(예: Capsule)를 만들고, Rigidbody 컴포넌트를 추가합니다.

> 3.위 스크립트를 PlayerJump.cs로 저장 후 오브젝트에 붙입니다.

> 4.점프 힘 (jumpForce) 값 조절로 높이 테스트 가능.

> 5.Play 버튼 후 Space 키로 점프 테스트.
