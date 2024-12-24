---
title: "Unity 벡터 정규화(Vector Normalization)"
date: 2024-12-24 00:00:00 +0
categories: [Unity]
tags: [Vector]
use_math: true


---

# [Unity\] 벡터 정규화

# (Vector Normalization)란?

**벡터 정규화(Vecotr Normalization)** : 임의의 길이를 가진 벡터를 
해당 벡터의 방향만을 유지한 채 길이가 1인 단위 벡터로 바꾸는 것이다.

**단위 벡터** : 길이 혹은 크기가 1인 벡터를 의미한다

***

유니티에서는 벡터의 덧셈 연산을 이용하여 방향 벡터를 하나의 벡터로 만들고, 

이를 속도에 곱하면 전후좌우로 이동할 수 있을 뿐만 아니라 대각선으로도 이동할 수 있다.    

```c#
#예시 코드
Vector3 moveDir = (Vector3.forward * vertical) + (Vector3.right * horizontal);
translate.Translate(moveDirection * moveSpeed * Time.deltaTime);
```

<br/>

그러나 전후좌우로 이동할 때는 문제없지만 대각선으로 이동할 때는 속도가 더 빨라지는 현상이 발생한다.

이러한 문제가 발생하는 이유는 생각보다 간단하다.

<br/>

대각선 방향으로 이동할 경우

두 수직 및 수평 방향의 벡터를 함께 더하게 되므로 벡터의 합의 크기가 증가한다.    

<br/>

이는 **피타고라스의 정리**에 따라 대각선 벡터의 크기가 더 커지기 때문이다.   

<br/>

더 자세히 설명하겠다.

<br/>

***

<br/>

Vector라는 이름을 가진 2차원 벡터를 하나 생성하겠다.

$$
\vec{Vector} = (1,1)
$$

![image-20241224123110192](https://github.com/user-attachments/assets/7396d3a6-6fff-41d3-9198-9ce5615c9799)

이제 벡터의 크기를 구해야 하는데, 위 직각 삼각형의 빗변의 길이를 확인해 보면 된다.

빗변의 길이를 구하기 위해서는 **피타고라스 정리**를 사용하면 된다.

$$
a^2 + b^2 = c^2
$$

$$
1^2 + 1^2 = c^2 
$$

$$
c^2=2
$$

$$
c = \sqrt{2}
$$

따라서 c의 값은 √2 가 된다. 이 값이 방향을 (1,1)로 가지는 벡터의 크기 이다.

이제 이 값으로 벡터의 x,y를 각각 나누면 된다.

$$
\vec{\text{Vector}} = \left(1 ÷ \sqrt{2}, 1 ÷ \sqrt{2}\right) \\
$$

계산 값은

$$
\vec{\text{Vector}} \=\ (0.7071067812, 0.7071067812)
$$

위와 같이 나온다. 위 상태가 정규화가 완료된 상태이다.

이제 확인을 위해 검산을 해보면

$$
(0.7071067812 \times 0.7071067812) = 0.5000000000 \ + \ (0.7071067812 \times 0.7071067812) = 0.5000000000
$$

$$
0.5000000000 + 0.5000000000 = 1.0000000000 
$$

알맞게 나온다.

<br/>

***

<br/>

이제 다시 돌아와 

```c#
#예시 코드
Vector3 moveDir = (Vector3.forward * vertical) + (Vector3.right * horizontal);
translate.Translate(moveDirection * moveSpeed * Time.deltaTime);
```

위 문제를 해결하기 위해서 **벡터 정규화(Vecotr Normalization)**를 사용해야 한다는 것을 알았을 것이다. 

이제 코드를 아래와 같이 바꾸면

```c#
Vector3 moveDir = (Vector3.forward * vertical) + (Vector3.right * horizontal);

translate.Translate(moveDirection.normalized * moveSpeed * Time.deltaTime);
```

대각선으로 이동할 때도 전후좌우로 움직일 때와 같은 속도로 움직일 수 있게 된다
