# 코드

## 내 코드

```python
n,m = map(int, input().split())
board = []
result = []
for _ in range(n):
     board.append(list(input()))
for i in range(n-7): # 행
     for j in range(m-7): # 열
```

여기까지는 구현을 했는데

1행 BWBWBWBW

2행 WBWBWBWB

1행 후 2행을 어떻게 색칠할 것인지 막혀서 못풀었다.

1행과 2행을 하나의 문자열로 합쳐서 한 다리 건너서 같은 색으로 만들면 되나.. 싶기도 하고

글을 쓰는 지금 다시 보니까 1행1열의 색깔과 무조건 반대되게 칠하면 되는것이었다..

좀 더 연구해볼걸 아깝다..

우선 나는 다른 사람들의 답변을 참조해서 아래처럼 제출했다.

## 모범 코드

```python
n,m = map(int, input().split())
board = []
result = []
for _ in range(n):
     board.append(list(input()))
for i in range(n-7): # 행
     for j in range(m-7): # 열
          x,y=0,0 # x: 체스판 시작이 W일 경우 / y: 체스판 시작이 B일 경우
          for k in range(i,i+8):
               for l in range(j,j+8):
                    if (k+l)%2==0:
                         if board[k][l] != 'B':
                              x += 1
                         if board[k][l] != 'W':
                              y += 1
                    else:
                         if board[k][l] != 'W':
                              x += 1
                         if board[k][l] != 'B':
                              y += 1
          result.append(min(x,y))
print(min(result))
```

다시 풀어도 `if (k+l)%2==0` 부터 그 아래 수식을 생각해내지 못할 듯..

2차원배열이므로 아래와 같은 흐름으로 나아간다.

```
[0][0],[0][1],[0][2] 짝홀짝
[1][0],[1][1],[1][2] 홀짝홀
```

머리 속에 욱여넣고 또 써먹자
