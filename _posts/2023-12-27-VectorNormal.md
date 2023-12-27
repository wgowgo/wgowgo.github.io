---
layout: single
title:  "Unity 벡터 정규화(Vector Normalization)"
categories: Unity
tag: Vector
toc: true
#author_profile: true
#sidebar:
#    nav: "docs"
---

# [Unity\] 벡터 정규화(Vector Normalization)란?

##### 벡터 정규화란 벡터의 방향을 유지한 채로 벡터의 크기를 1로 만들어주는 과정이다.

```c#
Vector3 moveDir = (Vector3.forward * vertical) + (Vector3.right * horizontal);

translate.Translate(moveDirection * moveSpeed * Time.deltaTime);
```

벡터의 덧셈 연산을 이용하여 방향벡터를 하나의 벡터로 만들고 이를 속도에 곱하면 전후좌우로 이동할 수 있을 뿐만 아니라 대각선으로도 이동할 수 있다. 
그러나 대각선으로 이동할 때 속도가 더 빨라지는 현상이 발생한다. 
대각선 방향으로 이동할 경우, 두 수직 및 수평 방향의 벡터를 함께 더하게 되므로 벡터의 합의 크기가 증가한다. 
피타고라스의 정리에 따라 대각선 벡터의 길이가 더 커지기 때문이다.

대각선으로 이동할 때 
크기가 1인 벡터로 정규화하여 방향 성분만을 고려하면 문제를 해결할 수 있다.
이때 필요한 것이 벡터 정규화이다.

코드를 다음과 같이 바꾸면

```c#
Vector3 moveDir = (Vector3.forward * vertical) + (Vector3.right * horizontal);

translate.Translate(moveDirection.normalized * moveSpeed * Time.deltaTime);
```
대각선으로 이동해도 크기가 1로 변환되어 같은 속도로 이동할 수 있게 된다.
