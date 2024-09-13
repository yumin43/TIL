> 240913(금)

### 📍 빗물받기 게임 설명
드디어 1주차 강의를 다 듣고 빗물받기 게임을 완성했다! Unity프로그램에서 다뤄야 하는 부분은 까먹을 때마다 그때그때 찾아보면 익숙해지리라 생각하고 코드 위주로 기록해 보려고 한다.

#### 1. Rain.cs
- 랜덤한 위치의 빗방울을 생성한다. `Range`로 범위를 설정해주면 해당 범위 내의 랜덤 숫자를 생성할 수 있다.
x, y 변수에 랜덤한 숫자를 할당하고, `transform.position`과 `Vector3`을 사용하여 빗방울의 위치를 좌표로 지정한다.
    ```C#
    float x = Random.Range(-2.4f, 2.4f);
    float y = Random.Range(3.0f, 5.0f);

    transform.position = new Vector3(x, y, 0);
    ```
- 빗방울의 크기와 색을 지정한다. `Range` 함수를 통해 지정한 범위는 두 번째 숫자를 제외하고 범위가 설정되므로 (1, 3)이 아닌 (1,4)로 작성하였다.
    ```C#
    int type = Random.Range(1, 4);   
    ```

 - 조건문을 통해 랜덤으로 설정된 타입에 따라 빗방울의 크기, 점수, 색상을 지정한다. `Color` 함수를 사용할 때는 **RGB 값을 255f로 나눠줘야 한다.**
    ```C#
    if(type == 1)
        {
            size = 0.8f;
            score = 1;
            renderer.color = new Color(100 / 255f, 100 / 255f, 1f, 1f);     
        }
        else if(type == 2)
        {
            size = 1.0f;
            score = 2;
            renderer.color = new Color(130 / 255f, 130 / 255f, 1f, 1f);   
        }  
        else if(type == 3)
        {
            size = 1.2f;
            score = 3;
            renderer.color = new Color(150 / 255f, 150 / 255f, 1f, 1f);     
        } 
    ```
- size 변수에 할당된 빗방울의 크기를 `transform.localScale`과 `Vector3` 함수에 사용하여 빗방울의 크기를 지정한다.
    ```C#
    transform.localScale = new Vector3(size, size, 0);
    ```
  
#### 2. GameManager.cs

#### 1. RetryButton.cs

### 📍 내일 계획
- 오늘 TIL 내용 추가
- 1주차 과제
- 개발 환경 세팅에서 문제가 있어서 오늘 오전에 너무 많은 시간을 소모했다.🥹 내일은 쉬는날이지만 1주차 과제라도 완료하는걸로!! 더하면좋고,,,왜냐면 진도가 너무 많이 밀려있다공!