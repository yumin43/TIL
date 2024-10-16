> 241016(수)

# 📍 들어가며
2D 게임에서 stage를 선택하는 Scene을 ScrollView로 구현해보았다.
<br><br>
<img width="356" alt="ScrollView" src="https://github.com/user-attachments/assets/32034325-f22f-4317-92d3-d46f0dcc0438">

## ✓ ScrollView - ScrollRect 컴포넌트
<img width="315" alt="ScrollRect" src="https://github.com/user-attachments/assets/0efecbf5-a7bb-490a-876c-f0734c590fe1">
<br>

- ScrollView를 생성하면 자동으로 `ScrollRect` 컴포넌트가 생성된다. 
- 세로로 버튼을 배치할 것이기 때문에 Horizontal을 체크 해제, `Vertical`을 체크한다. 그리고 자동으로 생성되는 `Scrollbar Vertical`과 Scrollbar Horizontal 중 Horizontal은 제거한다.
- `Scroll Sensitivity` : 스크롤의 민감도를 설정하는 속성, 숫자가 클수록 스크롤이 더 민감해진다(더 쉽게 스크롤이 된다(?)).
  
## ✓ Content
- 이녀석도 ScrollView를 생성하면 Hierarchy 창에서 ScrollView 하위에 자동으로 생성된다. 나는 Content의 하위에 프리팹으로 등록해놓은 버튼이 생성되도록 구현했다.

- `Vertical Layout Group` 컴포넌트를 추가하여 버튼을 어떻게 배치할지 설정해준다.       
  <img width="319" alt="Content" src="https://github.com/user-attachments/assets/0d911774-2ed7-4755-a5c0-8c0956a97099">
  - Top과 Bottom Padding 값을 50으로 설정 - 버튼 전체가 일렬로 들어가는 Canvas의 위아래에 간격을 50만큼 준 것
  - Spacing 30 - 버튼 간 간격을 30으로 설정한 것


