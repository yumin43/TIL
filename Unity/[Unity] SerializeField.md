> 241018(금)

# 📍 들어가며
프로젝트를 진행하면서 `[SerializeField]`를 많이 활용해서 정리하게 되었다.
<br><br>


## ✓ SerializeField란?
- 유니티에서 C# 스크립트 내 변수를 public을 설정하면 inspector 창에 해당 변수가 보여 직접 할당이 가능함. private로 선언하면 inspector 창에서 보이지 않는데, 이 때 `SerializeFiled`로 설정해주면 private 변수이지만 inspector 창에서 보여진다.
- 다시 정리하면 유니티 에디터의 inspector 창에서 보고 싶지만, 다른 클래스에서 접근이 불가능하도록 설정하고 싶을 때 사용한다.
<br>

## ✓ SerializeField 사용 코드
```C#
public class StageButton : MonoBehaviour
{
  [SerializeField] private Button btn;
}


```


