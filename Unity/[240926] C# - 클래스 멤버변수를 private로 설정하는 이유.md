> 240926(목)

# 📍 들어가며
프로젝트 진행 중 다른 팀원분들의 코드를 보다가 클래스 내의 멤버에 대한 접근 제한자를 `public`으로 설정했을 때와 `private`로 설정했을 때의 차이점이 궁금해졌다.
둘의 차이점에 대한 개념은 알고 있었지만, 정확한 이유가 궁금해서 찾아보게 되었다.

## ✓ `public` 멤버 
- 접근 범위: **클래스 외부**에서도 해당 멤버에 접근 가능
- 장점: 간단하고 바로 접근할 수 있어 편리
- 단점: 외부에서 자유롭게 접근 및 수정이 가능하기 때문에 클래스의 일관성에 좋지 않다.
- 객체지향 언어의 캡슐화와 거리가 멀다.

## ✓ `private` 멤버
- 접근 범위: **클래스 내부**에서만 해당 멤버에 접근 가능
- 장점: 외부에서 변수에 대한 직접적인 수정이 불가능하기 때문에 클래스의 일관성 유지 가능
- 단점: 멤버변수에 간접적으로 접근하기 위해서는 get/set 프로퍼티를 사용해야 한다.

❗️ 접근 제한자를 지정하지 않으면 디폴트는 `private`


## ✓ 예제

- get, set 프로퍼티 기반 코드

```C#
class Player
{
    private int hp;
    public int HP 
    { 
        get { return hp; }
        set { hp = value;} 
    }
}
static void Main(string[] args)
{
    Player player = new Player();
    player.Hp = 100;
    int myHp = player.Hp;
}
```

- get, set **자동 구현** 프로퍼티 기반 코드
```C#
class Player
{
    private int hp;
    public int HP { get; set; }
}
static void Main(string[] args)
{
    Player player = new Player();
    player.Hp = 100;
    int myHp = player.Hp;
}
```

❓ 자동 구현 프로퍼티는 그냥 public으로 변수를 선언한 경우와 무슨 차이인가

-> 큰 차이가 없다. 하지만 읽기-쓰기 전용, 읽기 전용 또는 쓰기 전용으로 프로퍼티의 유형을 설정할 수 있다. 
- get 프로퍼티만 지정하면 읽기전용
- set 프로퍼티만 지정하면 쓰기전용
- 둘 다 지정하면 읽기-쓰기 전용
- 위에 3가지 경우는 클래스 내부에서도 불가능
- get/set 앞에 private를 선언하여 외부에서 get/set을 할 수 없도록 구현 가능(위 3가지 경우는 set만 지정하는 건 불가능함 뭐 이런 얘기가 있어서.. 그냥 set 앞에 private 붙여서 쓰자.)

## ✓ `{ get; set; }`의 사용 이유
- 값을 get하거나 set할 때 조건을 걸어줄 수 있음
- 특별한 조건을 넣지 않아도 된다면 public으로 선언하여 사용하는것이 성능에 더 유리하다. 하지만 거의 차이가 없기 때문에 `private`를 사용하는 것이 좋다.(프로젝트 관리 측면에서)
- private 사용 이외에도 get/set 프로퍼티를 사용하여 `{get; private set}`을 통해 외부에서 값을 변경하지 못하도록 하는 것도 좋다.


## ✓ 추가로 알게된 부분🫢
- 클래스 내부에서만 접근이 가능한 private 변수를 선언하고, 클래스 외부에서도 접근 가능한 public 변수도 선언한 후 외부에서 private 변수에 접근할 수 있는 수단으로 함수를 만든다. 이렇게 되면 클래스 내부에서만 함수를 통해 private 변수에 접근할 수 있다.

- private에 get, set을 붙이는 게 아니라, private 변수에 접근 가능한 public 변수에 get, set을 붙이는거다.

<br>

# 📍 내일 계획
- 프로젝트 진행
- 오늘 TIL 작성한 거 질문!!(⭕️)
- 10일 만에 TIL을 작성하는 나 자신을 반성하며 앞으로는 빼먹지 않고 조금이라도 작성하기!!를 목표로 삼자.

<br>

## 참고
https://velog.io/@backfox/getter-%EC%93%B0%EC%A7%80-%EB%A7%90%EB%9D%BC%EA%B3%A0%EB%A7%8C-%ED%95%98%EA%B3%A0-%EA%B0%80%EB%B2%84%EB%A6%AC%EB%A9%B4-%EC%96%B4%EB%96%A1%ED%95%B4%EC%9A%94#1%EB%8B%A8%EA%B3%84--%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EC%88%98%EC%A0%95-%EB%AA%BB%ED%95%98%EA%B2%8C-%EB%A7%89%EA%B8%B0

- getter 사용을 지양하는 것이 좋다는 의견은 내 TIL 에서는 논외이긴 하지만 그래도 이해하는 데 도움이 됐던 멋진 글!!!
- 이 글을 완전히 이해할 수는 없지만 언젠가 어렵지 않게 이해할 수 있는 날이 오겠지~
