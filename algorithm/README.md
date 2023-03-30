# algorithm

## 목차
### [1. 시간 복잡도와 공간 복잡도를 알고 있는가?](#1-시간-복잡도와-공간-복잡도를-알고-있는가-1)
### [2. 정렬 알고리즘에 대해 알고 있는가?](#2-정렬-알고리즘에-대해-알고-있는가-1)
### [3. 이진 탐색에 대해 알고 있는가?](#3-이진-탐색에-대해-알고-있는가-1)
### [4. 연결 리스트에 대해 알고 있는가?](#4-연결-리스트에-대해-알고-있는가-1)
### [5. 스택, 큐에 대해 알고 있는가?](#5-스택-큐에-대해-알고-있는가-1)
### [6. 재귀에 대해 알고 있는가?](#6-재귀에-대해-알고-있는가-1)
### [7. 동적 계획법에 대해 알고 있는가?](#7-동적-계획법에-대해-알고-있는가-1)
### [8. 그리디 알고리즘에 대해 알고 있는가?](#8-그리디-알고리즘에-대해-알고-있는가-1)
### [9. DFS와 BFS에 대해 알고 있는가?](#9-dfs와-bfs에-대해-알고-있는가-1)
### [10. 해시 테이블에 대해 알고 있는가?](#10-해시-테이블에-대해-알고-있는가-1)
### [11. 트리와 이진트리에 대해 알고 있는가?](#11-트리와-이진트리에-대해-알고-있는가-1)


---
## 1. 시간 복잡도와 공간 복잡도를 알고 있는가?

- 시간 복잡도 : 알고리즘을 실행하는 데 필요한 시간의 양을 말합니다. 이를 Big O 표기법으로 나타내며, 알고리즘이 <br />
데이터의 양이 증가할 때 어떻게 실행 시간이 증가하는지를 나타냅니다.
- O(1): 상수 시간 복잡도입니다. 입력 크기가 어떻든 실행 시간이 일정합니다. <br />
ex) 배열의 인덱스를 통한 원소의 접근
- O(log n): 로그 시간 복잡도입니다. 입력 크기가 증가할 때 실행 시간이 로그 함수의 값에 비례하여 증가합니다. <br />
ex) 이진 검색
- O(n log n): 로그 선형 시간 복잡도 입니다. 입력 크기가 증가할 때, 실행 시간이 n과 log n의 곱에 비례하여 증가합니다. <br />
ex) 병합 정렬, 퀵 정렬
- O(n^2): 이차 시간 복잡도 입니다. 입력 크기가 증가할 때, 실행 시간이 입력 크기의 제곱에 비례하여 증가합니다. <br />
ex) 버블 정렬, 선택 정렬
- O(2^n): 지수 시간 복잡도 입니다. 입력 크기가 증가할 때, 실행 시간이 2의 n승에 비례하여 증가합니다. <br />
ex) 피보나치 수열을 계산하는 재귀 함수 
- 공간 복잡도: 알고리즘이 실행될 때 필요한 메모리의 양을 말합니다. 공간 복잡도 역시 Big O 표기법으로 나타냅니다.

<br />

### 1-1. Big O란 무엇인가?

- 알고리즘의 실행 시간 등을 최악으로 가정 했을 때를 의미합니다.

### [목차로 이동](#목차)

---

## 2. 정렬 알고리즘에 대해 알고 있는가?

- 버블 정렬 : 인접한 두개의 원소를 비교하면서 정렬을 수행하는 알고리즘입니다. 리스트의 왼쪽 끝부터 시작해서 인접한 두 원소를 <br />
비교하고, 만약 두 원소의 순서가 잘못되어 있다면 위치를 바꿉니다. 이렇게 마지막 원소까지 비교하면서 순서를 바꿉니다. <br />
버블 정렬의 시간 복잡도는 O(n^2)입니다. 첫 번째 원소의 자리를 찾으면, 두 번재 원소의 자리를 찾는 식으로 진행 됩니다. <br />

```
function bubbleSort(arr) {
  const len = arr.length;
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        const temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  return arr;
}
```

<br />

- 선택 정렬 : 주어진 배열에서 최솟값을 찾아 맨 앞에 있는 원소와 자리를 바꾸고, 다음으로 작은 값을 찾아서 그 다음 자리에 있는 <br />
원소와 자리를 바꾸고, 다음으로 작은 값을 찾아서 그 다음 자리에 있는 원소와 자리를 바꾸는 과정을 반복하는 알고리즘 입니다. <br />
시간 복잡도는 O(n^2)입니다. 배열 내에서 가장 작은 값을 찾아 맨 앞에 배치하고, 다시 반복문을 돌려 2번째로 작은 값을 찾아 <br />
두 번째에 배치하는 식으로 진행 됩니다.

```
function selectionSort(arr) {
  const len = arr.length;
  for (let i = 0; i < len; i++) {
    let min = i;
    for (let j = i + 1; j < len; j++) {
      if (arr[j] < arr[min]) {
        min = j;
      }
    }
    if (min !== i) {
      const temp = arr[i];
      arr[i] = arr[min];
      arr[min] = temp;
    }
  }
  return arr;
}
```
<br />

- 삽입 정렬 : 정렬 대상 배열을 정렬된 배열과 비교하여 위치를 찾아 삽입해가는 알고리즘입니다. <br />
시간 복잡도는 O(n^2)입니다. 배열을 두 가지 공간으로 나눕니다. 정렬이 된 공간은 왼쪽, 정렬이 <br />
되지 않은 공간은 오른쪽이라고 가정합니다. 정렬이 되지 않은 공간에서 숫자를 하나 뽑아 <br />
정렬이 된 왼쪽 공간을 순회하며 크기를 비교합니다. 뽑힌 수보다 클 경우 오른쪽으로 한칸 <br />
이동시킵니다. 더이상 뽑힌 수보다 큰 수가 존재하지 않을 때까지, 숫자를 이동시킨 후 <br />
뽑힌 수를 남은 공간에 집어 넣습니다.

```
function insertionSort(arr) {
  const len = arr.length;
  for (let i = 1; i < len; i++) {
    const current = arr[i];
    let j = i - 1;
    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }
    arr[j + 1] = current;
  }
  return arr;
}
```

- 퀵 정렬 : 주어진 배열을 두 개로 분할하고, 각각을 정렬하는 방식으로 동작합니다. <br />
시간 복잡도는 최악의 경우 O(n^2)이지만, 평균적으로는 O(nlogn)의 시간 복잡도를 가집니다. <br />
배열에서 하나의 원소를 피벗으로 선택합니다. 피벗보다 작은 수는 왼쪽 배열로, 큰 수는 <br />
오른쪽 배열에 넣습니다. 왼쪽 배열과, 오른쪽 배열에서 이러한 과정을 재귀적으로 실행합니다. <br />
피벗으로 최댓값, 최솟값이 계속 선택될 경우, 시간이 많이 걸리게 되지만 이러할 경우가 반복되기는 <br />
쉽지 않기 때문에 평균의 시간 복잡도를 언급하게 됩니다.

```
function quickSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const pivot = arr[0]; // 피벗으로 첫 번째 원소를 선택
  const left = [];
  const right = [];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }

  return quickSort(left).concat(pivot, quickSort(right));
}
```

<br />

- 병합 정렬 : 정렬한 리스트를 반으로 분할하고, 각각의 부분 리스트를 재귀적으로 병합하여 정렬하는 방식으로 동작합니다. <br />
시간 복잡도는 O(nlogn)입니다. 하지만 정렬한 리스트를 복사해서 저장해야 하므로 추가적인 메모리 공간이 필요하다는 단점이 있습니다. <br />
배열을 반으로 계속 쪼개 요소가 1개가 남을 때까지 나눕니다. 그리고 잘게 쪼개진 배열들을 합쳐 나가면서 정렬을 진행합니다. <br />

```
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const middle = Math.floor(arr.length / 2);
  const left = arr.slice(0, middle);
  const right = arr.slice(middle);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  let result = [];

  while (left.length && right.length) {
    if (left[0] <= right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }

  while (left.length) {
    result.push(left.shift());
  }

  while (right.length) {
    result.push(right.shift());
  }

  return result;
}
```

<br />

- 힙 정렬 : 최대 힙 또는 최소 힙을 이용하여 정렬하는 알고리즘입니다. 힙은 트리 자료 구조의 일종으로 부모 노드와 자식 노드 간에 <br />
대소 관계가 정해져 있는 특징을 갖습니다. 시간 복잡도는 O(nlogn)입니다. <br />
maxHeap을 구현하여 가장 큰 값을 찾습니다. 찾은 최대 값을 배열의 맨뒤로 보냅니다. <br />
맨뒤로 보낸 값을 제외하고 다시 maxHeap을 통해 최대 값을 찾고 배열의 2번째 뒤로 보냅니다. 이를 반복합니다 

```
function heapSort(arr) {
  const n = arr.length;

  // max heap 구조 만들기
  for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
    heapify(arr, n, i);
  }

  // heap 정렬 수행
  for (let i = n - 1; i > 0; i--) {
    // 현재 가장 큰 값(루트)을 맨 뒤로 보낸다
    const temp = arr[0];
    arr[0] = arr[i];
    arr[i] = temp;

    // heapify 수행
    heapify(arr, i, 0);
  }
  return arr;
}

function heapify(arr, n, i) {
  let largest = i;
  const left = 2 * i + 1;
  const right = 2 * i + 2;

  // 왼쪽 자식이 부모보다 크면 largest를 왼쪽 자식으로 업데이트
  if (left < n && arr[left] > arr[largest]) {
    largest = left;
  }

  // 오른쪽 자식이 부모보다 크면 largest를 오른쪽 자식으로 업데이트
  if (right < n && arr[right] > arr[largest]) {
    largest = right;
  }

  // largest가 부모가 아니면 교환 후 다시 heapify를 수행
  if (largest !== i) {
    const temp = arr[i];
    arr[i] = arr[largest];
    arr[largest] = temp;

    heapify(arr, n, largest);
  }
}
```

<br />


### [목차로 이동](#목차)

---


## 3. 이진 탐색에 대해 알고 있는가?

- 이진 탐색은 정렬된 배열에서 특정한 값을 찾는 알고리즘입니다. 배열의 중간 인덱스 값을 기준으로 찾고자 하는 값과 비교하여 <br />
탐색 범위를 반으로 줄여가며 찾아가는 방식으로 동작합니다. 시간 복잡도는 O(log n)으로 매우 빠릅니다. 주어진 배열이 <br />
정렬이 되어 있어야 합니다.

```
function binarySearch(arr, target) {
  let low = 0;
  let high = arr.length - 1;

  while (low <= high) {
    const mid = Math.floor((low + high) / 2);

    if (arr[mid] === target) {
      return mid;
    } else if (arr[mid] < target) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return -1; // 탐색 실패
}
```

<br />

### [목차로 이동](#목차)

---

## 4. 연결 리스트에 대해 알고 있는가?


- 연결 리스트는 데이터의 나열을 메모리 상에서 표현하는 자료구조 중 하나입니다. 데이터를 저장하는 <br />
노드들이 연결된 구조로 되어 있으며, 각 노드는 데이터와 다음 노드를 가리키는 포인터로 이루어져 있습니다. <br />
- 연결리스트의 특징은 다음과 같습니다.
- 순서가 있는 데이터의 집합을 저장할 수 있다.
- 메모리 상에서 연속적인 공간을 필요로 하지 않는다.
- 각 노드가 다음 노드를 가리키는 포인터를 가지고 있기 때문에 데이터의 삽입, 삭제가 용이 하다.
- 노드를 추가할 때마다 동적으로 메모리를 할당받아야 하기 때문에 메모리 공간을 더 많이 필요로 한다.

```
class Node {
  constructor(data, next = null) {
    this.data = data;
    this.next = next;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  append(data) {
    const newNode = new Node(data);

    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }

    this.length++;
  }

  insertAt(data, index) {
    if (index < 0 || index > this.length) {
      throw new Error('Invalid index');
    }

    const newNode = new Node(data);

    if (index === 0) {
      newNode.next = this.head;
      this.head = newNode;
    } else if (index === this.length) {
      this.tail.next = newNode;
      this.tail = newNode;
    } else {
      let prev = null;
      let current = this.head;
      let i = 0;

      while (i < index) {
        prev = current;
        current = current.next;
        i++;
      }

      newNode.next = current;
      prev.next = newNode;
    }

    this.length++;
  }

  removeAt(index) {
    if (index < 0 || index >= this.length) {
      throw new Error('Invalid index');
    }

    let removedNode;

    if (index === 0) {
      removedNode = this.head;
      this.head = this.head.next;
      if (this.length === 1) {
        this.tail = null;
      }
    } else if (index === this.length - 1) {
      let current = this.head;
      while (current.next !== this.tail) {
        current = current.next;
      }
      removedNode = this.tail;
      current.next = null;
      this.tail = current;
    } else {
      let prev = null;
      let current = this.head;
      let i = 0;

      while (i < index) {
        prev = current;
        current = current.next;
        i++;
      }

      removedNode = current;
      prev.next = current.next;
    }

    this.length--;
    return removedNode.data
```

<br />

### [목차로 이동](#목차)

---

## 5. 스택, 큐에 대해 알고 있는가?

- 스택: 데이터를 한 쪽 끝에서만 삽입하고 삭제할 수 있는 후입선출 구조의 자료 구조입니다. 블럭처럼 쌓인다고 볼 수 있습니다. <br />
ex) 웹 브라우저의 방문 기록을 뒤로 가기 버튼으로 이동할 때 사용 됩니다.

- 큐: 데이터를 한 쪽 끝에서 삽입하고, 다른 쪽 끝에서는 삭제할 수 있는 선입선출 구조의 자료 구조 입니다. <br />
ex) 티켓 구매열을 예시로 들 수 있습니다.

<br />

### [목차로 이동](#목차)

---

## 6. 재귀에 대해 알고 있는가?

- 재귀란 함수가 자기 자신을 호출하여 작업을 수행하는 것을 말합니다.
- 재귀를 사용할 때는 무한 루프에 빠지지 않도록 해야 합니다. 따라서 종료 조건을 꼭 명시해야 합니다.
- 또한 재귀 호출의 깊이가 너무 깊어지지 않도록 해야 합니다. 주어진 문제에 대한 해결에 대해 재귀의 호출이 너무 깊어진다면 <br />
문제에 대한 접근을 다시 해보는 것이 좋습니다.

<br />

### [목차로 이동](#목차)

---

## 7. 동적 계획법에 대해 알고 있는가?

- 큰 문제를 작은 문제로 나누어 해결하고, 그 결과를 저장하여 중복 계산을 피하는 알고리즘 설계 기법 입니다.
- 일반적으로 메모이제이션 기법을 사용합니다.
- 대표적인 예로 피보나치 수열 문제가 있습니다.

```
function fibonacci(n) {
  const memo = [0, 1];
  
  for (let i = 2; i <= n; i++) {
    memo[i] = memo[i - 1] + memo[i - 2];
  }
  
  return memo[n];
}
```

<br />

### 7.1 메모제이션 기법이란 무엇인가?

- 이미 계산된 값을 저장해 두고, 나중에 같은 계산이 필요할 때 이전에 계산한 값을 재사용하는 기법을 말합니다.

<br />

### [목차로 이동](#목차)

---

## 8. 그리디 알고리즘에 대해 알고 있는가?

- 최적해를 구하기 위해 매 단계에서 최적이라고 생각되는 선택을 하는 알고리즘입니다.
- 예를 들어, 돈을 거슬러줘야하는 문제일 경우, 가장 큰 금액으로 우선적으로 거슬러 주는 방법을 사용합니다.
- 하지만 그 결과가 항상 최적의 해가 아닐 수는 있다는 점을 유의해야 합니다. 결과적으로의 최선이 아닌 현재에서의 최선에 맞추어 <br />
진행을 하기 때문입니다.
- 예를 들어, 1원, 3원, 4원의 동전이 있을 때, 총 6원을 거슬러야 한다고 가정해 봅시다. 그리디 알고리즘을 통하면 4원 1개, 1원 2개 <br />
를 거슬러 줘야 합니다. 하지만 동전을 가장 적게 쓰려면 3원 2개로도 가능합니다. 

<br />

### [목차로 이동](#목차)

---

## 9. DFS와 BFS에 대해 알고 있는가?

- DFS, BFS는 그래프 탐색 알고리즘입니다. 경로 탐색이라고도 부릅니다.
- DFS: 깊이를 우선적으로 탐색합니다. 한 노드에서 시작하여 가능한 멀리까지 이동한 뒤, 다시 돌아와서 다른 방향의 노드를 탐색하는 방식입니다. <br />
스택 혹은 재귀 함수를 이용해 구현할 수 있습니다.
- 미로 찾기 같은 문제에서 목적지까지 가는 경로가 존재하는지 여부 확인하는 문제에서 사용할 수 있습니다.

```
// 그래프의 인접 리스트 표현 방법
const graph = {
  A: ['B', 'C'],
  B: ['A', 'D'],
  C: ['A', 'G', 'H', 'I'],
  D: ['B', 'E', 'F'],
  E: ['D'],
  F: ['D'],
  G: ['C'],
  H: ['C'],
  I: ['C', 'J'],
  J: ['I'],
};

// DFS 함수
function dfs(graph, start) {
  const visited = []; // 방문한 정점을 저장할 배열
  const stack = [start]; // 스택에 시작 정점을 넣음

  // 스택이 빌 때까지 반복
  while (stack.length !== 0) {
    const n = stack.pop(); // 스택의 가장 위에 있는 정점을 꺼냄

    // 방문하지 않은 정점일 경우 방문 처리 후 인접한 정점들을 스택에 추가
    if (!visited.includes(n)) {
      visited.push(n);
      const sub = graph[n].filter((v) => !visited.includes(v)); // 방문하지 않은 인접한 정점들
      stack.push(...sub); // 스택에 추가
    }
  }

  return visited;
}

console.log(dfs(graph, 'A')); // ["A", "C", "I", "J", "H", "G", "B", "D", "F", "E"]
```

<br />

- BFS: 깊이를 우선으로 탐색합니다. 한 노드에서 시작하여 인접한 노드를 먼저 방문하고, 그 다음 인접한 노드들을 <br />
방문하는 방식입니다. 큐를 이용하여 구현할 수 있습니다.
- 최단 경로 찾기 문제에서 사용할 수 있습니다.

```
function bfs(graph, startNode) {
  const visited = new Set();  // 방문한 노드를 기록하기 위한 Set
  const queue = [startNode];  // 탐색을 위한 큐(queue)

  visited.add(startNode);  // 시작 노드를 방문 처리

  while (queue.length > 0) {  // 큐가 빌 때까지 반복
    const node = queue.shift();  // 큐에서 노드를 하나 꺼냄
    const neighbors = graph[node];  // 현재 노드와 인접한 노드들

    for (let i = 0; i < neighbors.length; i++) {
      const neighbor = neighbors[i];

      if (!visited.has(neighbor)) {  // 방문하지 않은 인접 노드라면
        visited.add(neighbor);  // 방문 처리
        queue.push(neighbor);  // 큐에 추가
      }
    }
  }

  return visited;  // 방문한 노드들을 반환
}
```

<br />

### [목차로 이동](#목차)

---

## 10. 해시 테이블에 대해 알고 있는가?

- 키와 값 쌍으로 이루어진 데이터를 저장하고, 이를 빠르게 검색할 수 있도록 구현된 구조입니다.
- 검색과 삽입에 있어 평균적으로 O(1)의 시간 복잡도를 가집니다.
- 자바스크립트에서는 Map으로 구현할 수 있습니다.
- set(key, value): key-value 쌍을 추가합니다.
- get(key): key에 해당하는 value를 반환합니다.
- has(key): key가 존재하는지 여부를 반환합니다.
- delete(key): key가 해당하는 key-value 쌍을 삭제합니다.
- clear(): 모든 key-value 쌍을 삭제합니다.
- size: key-value 쌍의 개수를 반환합니다.


### 10-1. Set이란 무엇인가?

- 중복되지 않는 값들의 모음을 나타내는 자료 구조입니다.
- 순서를 유지하며, 추가된 순서대로 요소에 접근할 수 있습니다.
- 중복 요소를 허용하지 않기 때문에, 배열에서 중복 값을 제거할 때 사용할 수 있습니다.
- add(value): Set에 새로운 값을 추가합니다.
- delete(value): Set에서 값을 제거합니다.
- has(value): Set에 주어진 값이 존재하는지 여부를 반환합니다.
- size: Set에 저장된 값의 개수를 반환합니다.

<br />

### [목차로 이동](#목차)

---

## 11. 트리와 이진트리에 대해 알고 있는가?

- 트리는 데이터 구조에서 계층 구조를 나타내는 비선형 자료 구조입니다. 이진 트리는 각 노드가 최대 두 개의 자식 노드를 가지는 트리입니다.
- 탐색, 삽입, 삭제가 빠릅니다.
- 계층적 구조를 가져 데이터 분류, 정렬, 검색에 용이합니다.

<br />

### [목차로 이동](#목차)

---

