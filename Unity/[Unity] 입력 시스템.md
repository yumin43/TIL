> 241011(금)

## ✓ Rigidbody 컴포넌트
- GameObject가 물리 제어로 동작할 수 있도록 하는 컴포넌트

## ✓ GetAxis 메소드
- 유니티의 입력 시스템에서 사용되는 메소드
- -1 ~ 1 사이의 입력 축의 값을 반환
- 주로 플레이어의 움직임, 회전, 점프 등을 처리하는데 사용됨
- GetAxis 메소드를 사용하여 수평, 수직 압력에 따라 오브젝트가 움직이도록 할 수 있음
```C#
float vertical = Input.GetAxis("Vertical");     // 수직 이동
float horizontal = Input.GetAxis("Horizontal"); // 수평 이동

Vector2 direction = new Vector2(horizontal, vertical);
```
❗️ 따옴표 내 오타 주의!!
- `GetAxis` 메소드보다 즉각적인 반응이 필요한 경우 `GetAxisRaw` 메소드를 사용하면 된다. 

## ✓ velocity
- Rigidbody 컴포넌트의 속도를 나타내는 변수
- 벡터값을 설정해주면 해당 방향으로 움직임
```C#
GetComponent<Rigidbody2D>.velocity = new Vector2(xSpeed, ySpeed);
```

<br>

# 📍 내일 계획
- 강의 다 듣고 개인과제 시작