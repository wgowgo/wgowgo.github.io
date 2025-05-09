---
title: "자료구조 - 리스트, 배열"
date: 2025-05-09 00:00:00 +0
categories: [Data Structure]
tags: [List, Array]
use_math: true


---

# 자료구조 - (List, Array)란?

***

자료구조 - 리스트(List)와 배열(Array)
프로그래밍을 시작하면 가장 먼저 접하게 되는 자료구조가 바로 **배열(Array)**과 **리스트(List)**입니다. 
이 둘은 실생활의 장보기 목록이나 오늘 할 일 목록처럼 순서를 가진 데이터의 집합이라는 점에서 매우 유사하지만, 
내부 구조와 동작 방식에서는 명확한 차이가 있습니다.

이번 글에서는 리스트와 배열의 개념, 구현 방식, 장단점 비교, C++ 기준의 예제 코드까지 전반적으로 살펴보겠습니다. 
자료구조를 처음 공부하는 분들에게 두 구조 모두 꼭 짚고 넘어가야 할 필수 개념입니다.

1. 리스트란 무엇인가?
리스트(List)는 순서가 있는 데이터의 집합입니다. 즉, 각 데이터(원소)는 특정한 위치(인덱스)를 가지며, 순서를 통해 참조할 수 있습니다.
이 순서의 개념 덕분에 리스트는 수열(sequence)과 유사하다고도 볼 수 있습니다.

순서 보장: 데이터 삽입 순서대로 정렬

중복 허용: 동일한 값의 원소를 여러 번 저장 가능

동적 크기: 구현에 따라 크기를 유동적으로 조절 가능

우리가 평소 사용하는 장보기 리스트나 To-Do 리스트처럼, 순서를 가지며 여러 항목을 묶어서 다룰 수 있는 것이 리스트입니다.

2. 배열이란 무엇인가?
배열(Array)은 같은 자료형의 데이터를 연속적으로 저장하는 자료구조입니다. 각 원소는 인덱스를 가지며, 0부터 시작하여 순서대로 접근할 수 있습니다.

정적 크기: 선언 시 크기가 고정됨

연속된 메모리 구조: 물리적으로 연속된 메모리 공간 차지

빠른 인덱스 접근: O(1) 시간에 임의 원소 접근 가능

3. 리스트와 배열의 구현 방식
리스트는 구현 방식에 따라 크게 두 가지로 나눌 수 있습니다:

3-1. 순차 리스트 (배열 기반 리스트)
순차 리스트는 **배열(Array)**을 기반으로 구현된 리스트입니다. 물리적으로 메모리 상에서 연속된 공간을 차지하며, 인덱스를 통해 직접 접근할 수 있다는 점이 특징입니다.

장점:

인덱스를 통한 빠른 접근 (O(1))

구현이 간단하고 이해하기 쉬움

단점:

삽입/삭제 시 원소 이동 필요 (O(n))

크기 변경이 어렵고, 배열 재할당이 필요할 수 있음

3-2. 연결 리스트 (Linked List)
연결 리스트는 **포인터(링크)**를 활용하여 각 데이터를 연결하는 방식입니다. 메모리 상에서 물리적으로 연속되지 않은 위치에 데이터를 저장하며, 각 노드는 다음 노드를 가리키는 포인터를 가집니다.

장점:

삽입/삭제가 빠름 (O(1), 포인터 변경만으로 처리)

크기 제약 없음, 동적 메모리 관리에 유리

단점:

특정 원소 접근 시 순차 탐색 필요 (O(n))

구현이 복잡하며, 메모리 사용량 증가

4. 배열과 리스트의 비교
항목	배열 (Array)	리스트 (List)
구조	연속된 메모리 구조	연결 구조 or 동적 구조
크기	고정 크기	유동적 크기 가능
접근 속도	빠름 (O(1))	배열 기반은 빠름, 연결 리스트는 느림
삽입/삭제	느림 (O(n))	연결 리스트는 빠름
구현 복잡도	낮음	연결 리스트는 높음

5. 연결 리스트의 종류
연결 리스트는 포인터의 방향성과 구조에 따라 다음과 같이 나뉩니다:

단일 연결 리스트 (Singly Linked List)
각 노드가 다음 노드를 가리키며, 마지막 노드는 NULL을 가리킵니다.

원형 연결 리스트 (Circular Linked List)
마지막 노드가 다시 첫 노드를 가리켜 시작과 끝의 경계가 없습니다.

이중 연결 리스트 (Doubly Linked List)
각 노드가 이전 노드와 다음 노드를 모두 가리킵니다. 양방향 탐색이 가능하지만 메모리 사용량이 더 큽니다.

6. C++ 예제로 살펴보는 배열과 리스트
6-1. 배열 예제


#include <iostream>
using namespace std;
int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; ++i)
        cout << arr[i] << " ";  // 출력: 10 20 30 40 50

    return 0;
}
6-2. 2차원 배열 예제


#include <iostream>
using namespace std;
int main() {
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    for (int i = 0; i < 2; ++i) {
        for (int j = 0; j < 3; ++j)
            cout << matrix[i][j] << " ";
        cout << endl;
    }

    // 출력:
    // 1 2 3
    // 4 5 6

    return 0;
}
6-3. 순차 리스트 예제 (std::vector)


#include <iostream>
#include <vector>
using namespace std;
int main() {
    vector<int> list;
    list.push_back(10);
    list.push_back(20);
    list.insert(list.begin() + 1, 15); // 1번 인덱스에 삽입
    list.erase(list.begin()); // 첫 요소 삭제

    for (int val : list)
        cout << val << " ";  // 출력: 15 20
    return 0;
}
6-4. 단일 연결 리스트 예제

#include <iostream>
using namespace std;
struct Node {
    int data;
    Node* next;
    Node(int d) : data(d), next(nullptr) {}
};

class LinkedList {
    Node* head;
public:
    LinkedList() : head(nullptr) {}

    void append(int value) {
        if (!head) {
            head = new Node(value);
            return;
        }
        Node* cur = head;
        while (cur->next)
            cur = cur->next;
        cur->next = new Node(value);
    }

    void insert(int index, int value) {
        Node* newNode = new Node(value);
        if (index == 0) {
            newNode->next = head;
            head = newNode;
            return;
        }
        Node* cur = head;
        for (int i = 0; i < index - 1 && cur; i++)
            cur = cur->next;
        if (!cur) return;
        newNode->next = cur->next;
        cur->next = newNode;
    }

    void print() {
        Node* cur = head;
        while (cur) {
            cout << cur->data << " ";
            cur = cur->next;
        }
        cout << endl;
    }
};

int main() {
    LinkedList list;
    list.append(10);
    list.append(30);
    list.insert(1, 20);
    list.print(); // 출력: 10 20 30
    return 0;
}
7. 어떤 자료구조를 선택할까?
데이터 수가 고정되거나 예상 가능한 경우: 배열이 적합

빠른 인덱스 접근이 필요한 경우: 배열이 적합

빈번한 삽입/삭제가 필요한 경우: 배열은 비효율 → 연결 리스트 고려

데이터 크기 유동적, 삽입/삭제 빈번: 연결 리스트가 효율적

탐색 중심 작업: 순차 리스트

삽입/삭제 중심 작업: 연결 리스트

8. 마무리
리스트와 배열은 단순한 구조 같지만, 실제로는 수많은 자료구조와 알고리즘의 기반이 되는 매우 중요한 구조입니다. 특히 연결 리스트는 스택, 큐, 트리, 그래프 등 다양한 자료구조의 뼈대가 되기도 합니다. 배열은 많은 고급 자료구조의 내부 구조로도 활용되며, 빠른 접근성과 단순한 구조 덕분에 널리 사용됩니다.

언어마다 리스트와 배열을 지원하는 방법이 다르고, 라이브러리로 제공되는 경우도 많지만, 그 기본 개념과 작동 원리를 이해하는 것은 매우 중요합니다. 직접 구현을 해보며 내부 동작을 파악하는 것이 좋은 학습 방법입니다.

다음 글에서는 연결 리스트의 변형 구조들과 활용 예제, 그리고 실제로 쓰이는 스택이나 큐와의 연관성에 대해 더 깊이 있게 다뤄보도록 하겠습니다.

감사합니다!
