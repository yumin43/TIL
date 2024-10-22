> 241022(화)

## ✓ Scriptable Object란?
- 유니티에서 제공하는 데이터 저장소
- 사용 시 값의 사본이 생성되는 것을 방지하여 메모리 사용량을 줄일 수 있다.
- 오브젝트에 컴포넌트를 추가하는 방식이 아닌, Asset으로 프로젝트에 저장된다.
- 클래스가 Scriptable Object를 상속받는 방식으로 사용된다.
<br>

## ✓ Scriptable Object 사용 예시
- CreateAssetMenu: Scriptable Object 에셋을 빼르고 쉽게 생성할 수 있도록 만들어주는 속성
  - fileName: 생성 시 기본 파일명
  - menuName: 에셋 생성 경로
```C#
[CreateAssetMenu(fileName = "DefaultAttackSO", menuName = "TopDownController/Attack/Default", order = 0)]
```
- `ScriptableObject` 클래스를 상속받아 구현한다.
```C#
public class AttackSO : ScriptableObject
{
    [Header("Attack Info")]
    public float size;
    public float delay;
    public float power;
    public float speed;
    public LayerMask target;    
}
```


