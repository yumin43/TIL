> 241025(금)

# 📍 들어가며
플레이어의 Input System 구현 과정에서 정리하고 싶은 내용을 적어보았다.
<br><br>


## ✓ Update(), FixedUpdate(), LateUpdate()
- Move 함수 호출은 FixedUpdate에서, CameraLook 함수 호출은 LateUpdate에서 진행했는데 그 이유가 궁금해서 찾아보게 되었음!!

#### `Update()`
- 매 프레임마다 호출되며, 호출 간격이 일정하지 않다.
- 물리 효과가 적용되지 않은 오브젝트의 움직임이나, 단순 타이머 및 키 입력을 받을 때 주로 사용된다.

#### `FixedUpdate()`
- 설정된 값에 따라 일정한 간격으로 호출된다.
- 물리 효과가 적용된 object를 다룰 때 사용된다. (Update는 불규칙적으로 호출되기 때문에 물리엔진 충돌 검사 등이 제대로 수행되지 않을 수 있기 때문)

#### `LateUpdate()`
- 모든 Update 함수 호출 후 마지막으로 호출된다.
- 주로 오브젝트를 따라가도록 설정된 카메라는 LateUpdate를 사용한다. ( Update 함수에서 카메라가 따라가는 오브젝트의 움직임 처리를 한 후 LateUpdate 함수에서 카메라의 위치를 이동시키는 식으로 구현하기 때문)
<br>

## ✓ InputAction.CallbackContext
- OnMoveInput, OnLookInput, OnJumpInput 함수에 파라미터로 사용한 타입이다.
```C#
InputAction.CallbackContext context
```
- 해당 파라미터는 입력의 상태를 확인할 수 있다.
  - `context.started` - 입력이 시작되었을 때(한 번만 작동)
  - `context.performed` - 입력이 수행되었을 때
  - `context.canceled` - 입력이 취소되었을 때
  - 위 세 가지는 bool 타입을 반환한다.

## ✓ ForceMode
- Rigidbody타입변수.**AddForce** 함수 사용 시 매개변수로 적용하는 옵션으로, 힘의 종류를 나타내어 Rigidbody에게 힘을 전달해준다.
  - `ForceMode.Force` - 연속 + 질량무시X
  - `ForceMode.Acceration` - 연속 + 질량무시O
  - `ForceMode.Impulse` - 불연속 + 질량무시X
  - `ForceMode.VelocityChange` - 불연속 + 질량무시O
- 구현한 Input System에서 점프 효과를 위해 `ForceMode.Impulse`를 사용했다.
    ```C#
    public void OnJumpInput(InputAction.CallbackContext context)
    {
        if(context.started)
        {
            rigidbody.AddForce(Vector2.up * jumpPower, ForceMode.Impulse);
        }
    }
    ```
