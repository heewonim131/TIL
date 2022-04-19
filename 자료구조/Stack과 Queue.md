## Stack
- 맨 마지막 위치(top)에서만 요소를 추가,삭제, 꺼내올 수 있다.
- 제일 늦게 들어간 요소가 제일 먼저 나온다.
- Last In First Out (LIFO) 구조

Stack 은 직접 클래스를 제공한다.
```
Stack<Integer> stack = new Stack<>();
```
- `push()` : 요소 추가
- `pop()` : 요소 삭제
- `peek()` : 요소 조회

<br>

## Queue
- 맨 앞(front)에서 요소를 꺼내거나 삭제하고, 맨 뒤(rear)에서 요소를 추가한다.
- 제일 먼저 들어간 요소가 제일 먼저 나온다.
- Fist In First Out (FIFO) 구조


Queue 인터페이스를 구현한 클래스로는 LinkedList 등이 있다.
```
Queue<Integer> queue = new LinkedList<>();
```
- `offer()` : 요소 추가
- `poll()` : 요소 삭제
- `peek()` : 요소 꺼내기(조회)

<br>

## Deque
- 앞에서 요소를 꺼낼 수도, 뒤에서 요소를 꺼낼 수도 있다.

Deque 인터페이스를 구현한 클래스로는 LinkedList 등이 있다.
```
Deque<Integer> deque = new LinkedList<>();
```
- First Element (Head)
  - `offerFirst()` : 요소 추가
  - `pollFirst()` : 요소 삭제
  - `peekFirst()` : 요소 꺼내기(조회)


- Last Element (Tail)
  - `offerLast()` : 요소 추가
  - `pollLast()` : 요소 삭제
  - `peekLast()` : 요소 꺼내기(조회)

