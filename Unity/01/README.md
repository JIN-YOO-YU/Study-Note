# 유니티 기본 개념
+ Unity Editor 소개
> + Scene View: 게임 세계를 시각적으로 구성하는 공간입니다. 오브젝트의 배치, 이동, 회전, 스케일 등을 조작할 수 있습니다
> + Game View: 실제 플레이어가 보게 될 게임 화면을 미리보기로 확인할 수 있습니다
> + Hierarchy: 현재 씬(Scene)에 포함된 모든 GameObject를 계층 구조로 보여줍니다. 부모-자식 관계를 설정하거나 오브젝트를 추가 및 삭제할 수 있습니다
> + Inspector: 선택한 GameObject의 속성과 컴포넌트를 편집할 수 있는 창입니다. Transform, Collider 등 다양한 컴포넌트 정보를 확인하고 수정할 수 있습니다
> + Project: 프로젝트의 모든 파일과 에셋(Assets)을 관리하는 창으로, 폴더 구조를 통해 에셋을 정리하고 사용할 수 있습니다
+ 유니티의 주요 구성 요소
> + Scene: 게임의 특정 장면을 구성하는 공간. 각 장면은 여러 오브젝트로 이루어져 있습니다.
> + GameObject: 게임 내에서의 모든 객체를 말하며, 물리적, 시각적, 논리적 기능을 수행하는 기본 요소입니다.
> + Component: GameObject의 기능을 결정하는 요소로, 각 오브젝트에 부착하여 행동을 제어합니다. 예) Mesh Renderer, Collider, Rigidbody 등.
> + Asset: 게임에서 사용되는 다양한 자료들, 예를 들어 텍스처, 모델, 오디오 파일 등이 있습니다.
> + Prefab: 자주 사용되는 GameObject의 템플릿으로, 한번 설정한 객체를 여러 번 재사용할 수 있습니다.
+ 유니티 C# 스크립트 기본 구조
> 1. using UnityEngine;
> > + UnityEngine 네임스페이스를 사용하여 유니티에서 제공하는 클래스와 기능을 사용할 수 있게 됩니다. 예를 들어, GameObject, Transform, MonoBehaviour, Input, Time 등의 클래스가 이 네임스페이스에 포함되어 있습니다.
> 2. 클래스 선언: public class ExampleScript : MonoBehaviour
> > + 스크립트의 클래스는 반드시 MonoBehaviour를 상속받아야 합니다. MonoBehaviour는 유니티에서 객체와 상호작용할 수 있도록 하는 기본 클래스입니다.
> > + 클래스명은 스크립트 파일 이름과 동일해야 하며, 여기서는 ExampleScript라는 이름입니다.
> 3. public과 private 변수
> > + public: 이 변수는 유니티 에디터에서 조작할 수 있는 공개 변수입니다.
> > + private: 이 변수는 스크립트 내에서만 접근 가능한 비공개 변수입니다.
> 4. Start() 메서드
> > + Start()는 게임 오브젝트가 활성화된 후 첫 번째 프레임에서 한 번만 호출됩니다. 주로 초기화 작업을 여기에서 처리합니다.
> 5. Update() 메서드
> > + Update()는 매 프레임마다 호출되는 메서드입니다. 게임 로직에서 자주 사용되는 메서드로, 사용자 입력을 처리하거나 오브젝트의 이동, 애니메이션 등을 제어할 때 사용됩니다.
