> 241211(수)

# 📍 직면한 문제
게임 씬의 4X4 필드에 유닛을 드래그앤드롭을 통해 배치할 때, 유닛의 순서가 올바르게 배치되어야 하는데, 나중에 배치된 유닛들이 앞으로 오게 되는 문제가 있었다.

<img width="397" alt="스크린샷 2024-12-11 오후 9 59 56" src="https://github.com/user-attachments/assets/e43b202a-4fcb-415f-a075-a63ca2e0440f">
<br><br>


# 📍 해결 과정

## ✓ 원인 분석
- 배치하는 순서대로 Hierachy 창에 생성되기 때문(Hierachy 창에서 가장 아래쪽 오브젝트가 가장 앞에 배치됨)

## ✓ 시도 방법 1
- 빈 오브젝트 4개 생성
    - 기존에는 Characters라는 빈 오브젝트의 하위에 배치하는 순서대로 프리팹이 생성됨.
    - Characters 하위에 필드의 각 행을 나타내는 Group1, Group2, Group3, Group4 오브젝트를 추가 생성하여 각 오브젝트의 하위에 오브젝트를 생성하도록 코드를 수정함.
      - 이렇게 하면 가장 앞쪽 행에 배치된 유닛 프리팹이 Hiarachy 창의 가장 아래쪽에 생성되므로 가장 앞쪽에 배치될 것이라고 예상하였음.<br>

❗️ 결과
- Hiarachy 창의 순서에 영향을 받는 상황은 Canvas 내의 UI 요소일 때인데, 생성되는 유닛들은 UI가 아니기 때문에 문제가 해결되지 않음.

## ✓ 시도 방법 2
- 4개의 Group 오브젝트의 z position 값 조정
  - 각 Group 오브젝트를 Canvas로 변경하여 sort order 값을 조정하는 생각도 했었지만, 유닛 프리팹이 Rect Transform이 아닌 Transform이었기 때문에 z 값을 조정하기로 결정함
    - Group 1 : 14
    - Group 2 : 13
    - Group 3 : 12
    - Group 4 : 11


### 추가로 발생한 문제
- 그룹 오브젝트 하위에 생성되는 유닛 프리팹의 z값이 각각(-14, -13, -12, -11)로 자동 변경되는 문제 발생
- 해결 방법
  - 코드 수정 : position → localPosition
    ```C#
    // 기존 코드
    _character.transform.position = worldPosition;
    
    // 변경된 코드
    _character.transform.localPosition = worldPosition;
    ```
  - 기존 코드는 유닛 프리팹이 부모 오브젝트의 변화에 영향을 받기 때문에 0이어야 할 z 값이 부모 오브젝트 z값의 음수로 자동 변경되었다. (Group 1인 경우 유닛 프리팹의 z값 -14로 변경)
  - 따라서 부모 오브젝트의 영향을 받지 않기 위해 localPosition을 사용하여 해결하였다!

~~별것도아닌거같은데찾는데디게오래걸림삽질함~~

# 📍 결론
## ✓ position과 localPosition의 차이점
- `transform.position` 
  - 기준 좌표계: 월드 좌표(World Space)
  - 특징
    - 게임 월드에서의 절대적 위치
    - 부모 오브젝트의 이동/회전에 영향을 받음
- `transform.localPosition`
  - 기준 좌표계: 로컬 좌표(Local Space)
  - 특징
    - 부모 오브젝트를 기준으로 한 **상대적** 위치
    - 부모의 이동/회전에 따른 좌표 변화 없음