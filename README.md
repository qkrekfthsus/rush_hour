# rush_hour
![그림1](https://user-images.githubusercontent.com/60336758/114293947-9ac14100-9ad5-11eb-9664-ba29ce5a090c.png)

 이 문제는 보드게임인 “러시아워”의 규칙을 기본으로 하고 있습니다. 목표 블록을 출구로 이동시키면 이 게임에서 승리하게 됩니다. 먼저 이 문제는 4x4 공간에서 목표 블록 개와 방해 블록 3개로 구성되어있고 각 블록의 크기는 2x1입니다. 이 블록들은 모두 긴 방향으로만 이동할 수 있습니다.
 
 이 문제의 목표 상태는 목표 블록이 최소한의 블록들의 이동으로 출구로 도착하는 것입니다. 목표 상태까지의 블록들의 이동은 빨간 블록이 최고 우선순위이고 다른 블록들은 보드의 각각의 칸에 매겨진 평가 점수에 의해서 움직이게 됩니다.

![image](https://user-images.githubusercontent.com/60336758/114294040-423e7380-9ad6-11eb-8a39-53c02dd0494f.png)

 각각의 칸에 점수를 부여하고, 블록들로 그 칸들을 가려, 블록의 움직임이 실행되었을 때, 가려지지 않은 점수들의 합이 가장 높아지는 쪽으로 선택하게 하도록 하였습니다. 목표 상태로 도달할 수 있도록 점수판을 만들고, 세로 긴 블록들은 아래에 있어야 더 높은 점수를 받고, 방해하는 블록들이 뒤쪽에 있을수록 해당 상태의 점수는 더 높아도록 하였습니다. 가려지지 않은 칸의 점수들의 합이 가장 높아지는 선택을 할 수 있도록 하였습니다.

![image](https://user-images.githubusercontent.com/60336758/114294065-8b8ec300-9ad6-11eb-82e3-15ab5c6f64c4.png)&nbsp;&nbsp;&nbsp;&nbsp;![image](https://user-images.githubusercontent.com/60336758/114294085-cbee4100-9ad6-11eb-94ba-0855bc427da9.png)


 전체적인 부분에서 보면, 이 문제는 초기에 빨강 블록(왼쪽으로만 이동 가능)은 목표 상태에 도달할 때까지, 2차원 배열에 [“RED”, “LEFT”]의 값을 넣은 스택을 생성합니다. Python은 배열을 통해 쉽게 스택을 구현할 수 있으므로, 예를 들어 목표 상태에 도달하기 위해 3번의 움직임이 필요하다면, [[“RED”, “LEFT”], [“RED”, “LEFT”], [“RED”, “LEFT”]]이라는 스택을 생성합니다. 그리고 빨강 블록이 왼쪽으로 움직일 수 없다면, 다른 블록의 색깔과 움직이는 방향에 대한 정보를 담은 내용을 push 합니다. 아래의 그림에서는 노란 블록, 그리고 아래쪽을 담아 [[“RED”, “LEFT”], [“RED”, “LEFT”], [“RED”, “LEFT”], [“YELLOW”, “DOWN”]]의 내용이 스택에 담겨있는 모습을 볼 수 있습니다. 이 움직임들이 실행되면 pop을 통해 해당 내용을 지우게 됩니다. 그리고 스택을 비움으로써 문제를 해결할 수 있도록 하였습니다.

 다음은 파일별 함수에 대한 설명입니다.
 
![image](https://user-images.githubusercontent.com/60336758/114294147-79615480-9ad7-11eb-854b-a8f21b89c6d2.png)![image](https://user-images.githubusercontent.com/60336758/114294148-7c5c4500-9ad7-11eb-8124-09131cf14cb9.png)