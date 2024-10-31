> 241031(금)

## ✓ Trigger이란
- 유니티의 충돌 처리는 `Collision`과 `Trigger` 타입이 있으며, `Trigger`는 `Collision`과는 다르게 충돌 시 튕겨나가는 등의 물리 효과가 발생하지 않는 것이 가장 큰 차이점이다.
- 조건: 충돌하는 두 오브젝트 중 하나가 isTrigger 상태여야 함.
- 일반적으로 플레이어와 아이템이 상호작용하거나, 캐릭터가 영역에 진입한 경우 이벤트를 발생시키고자 할 때 사용된다.

## ✓ Trigger 관련 메소드
- `OnTriggerEnter(Collider other)` - 두 객체가 충돌할 때 호출되는 메소드
- `OnTriggerStay(Collider other)` - 두 객체가 충돌하는 동안 호출되는 메소드
- `OnTriggerExit(Collider other)` - 두 객체가 충돌을 끝마쳤을 때 호출되는 함수
