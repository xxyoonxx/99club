# 코드

## 내 코드

- 틀린 코드

```python
m = int(input())
n = int(input())
arr = [i for i in range(m,n+1)]
if m==1: arr.remove(1)
for i in arr:
    for j in range(2,i):
        flag = False
        if i%j==0:
            flag = True
            arr.remove(i)
        if flag : break
print(arr)
```

list에서 remove를 쓸 경우, remove로 제거 된 요소 뒤에 있는 요소들의 인덱스가 앞으로 당겨지게됨

즉, 요소[인덱스]라고 가정하고 표기하자면

```
       [0][1][2][3]
list = [1, 2, 3, 4]
list.remove(1)
       [0][1][2]
list = [2, 3, 4]
```

이런 식으로 변경되기 때문에 인덱스 0 다음 인덱스 1은 본래 의도하던 2가 아니고 3이 되게 된다.

따라서 내 코드로 실행하게 되면 출력값은 `[61, 63, 65, 67, 69, 71, 73, 75, 77, 79, 81, 83, 85, 87, 89, 91, 93, 95, 97, 99]` 이런식으로 2씩 비는 값을 받게 된다.

- 고친 코드

```python
m = int(input())
n = int(input())
arr = [i for i in range(m,n+1)]
if m==1: arr.remove(1)
# 슬라이싱을 사용하면 요소와 인덱스를 그대로 copy해서 가져오면서,
# remove에 직접적인 영향을 받지 않음
for i in arr[:]:
    for j in range(2,i):
        flag = False
        if i%j==0:
            flag = True
            arr.remove(i)
        if flag : break
print(arr)
```

**1도 소수가 아니니 주의**

## 모범 코드

```python
def is_prime_number(x):
    if x == 1:
        return False
    for i in range(2, int(math.sqrt(x)) + 1):
        if x % i == 0:
            return False
    return True

m = int(sys.stdin.readline())
n = int(sys.stdin.readline())
prime_numbers = []
for i in range(m, n + 1):
    if is_prime_number(i):
        prime_numbers.append(i)
if len(prime_numbers) == 0:
    print(-1)
else:
    print(sum(prime_numbers))
    print(min(prime_numbers))
```

# 회고

내 코드는 844ms가 걸렸는데 논리적으로 같이 접근했지만 시간이 적게 나온 코드들을 보니 아래와 같은 특징이 있었다.

- 함수를 사용
- if로 거른 후 for문을 사용

잘 익혀뒀다가 나중에 좀 더 심화 된 알고리즘을 풀 때 사용하자

2중 for문을 나갈 때 true, false 변수를 따로 이용하는 방법을 처음 사용해보았다.

자바스크립트에서는 몇 번 사용해봤는데 생각해내지 못해서 아쉽다.

# References

[[Python List] for loop 안에서 list.remove() 사용 시 주의할 점](https://taylor-kang.tistory.com/12)
