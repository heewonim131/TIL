## Array
```
int[] arr = new int[5];
```
- 배열의 요소들은 해당 자료형의 초기값으로 초기화된다.
- 배열 크기만큼의 연속된 메모리 영역이 할당된다.
- 배열을 출력하면 메모리 상의 배열 주소가 출력된다.
- 배열의 내용을 출력하려면 `Arrays.toString(arr)` 메서드를 사용한다.

### 👍 Array의 장점
- 여러개의 데이터를 한꺼번에 다룰 수 있다.
- 첫 번째 위치만 알면 index로 상대적 위치를 빠르게 찾을 수 있다.

### 👎 Array의 단점
- 한 번 만들어진 공간은 크기가 고정된다.
- 미리 공간을 확보해놓고 써야 한다.

## List
List는 유연하지 못한 Array의 단점들을 보완한다.  
List 인터페이스를 구현한 클래스로 LinkedList, ArrayList, Vector 등이 있다.
```
List<Integer> list = new LinkedList<>();
List<Integer> list = new ArrayList<>();
List<Integer> list = new Vector<>();
...
``` 
- List를 출력하면 List 내용이 출력된다.
- 특정 위치에 요소를 추가할 수 있다.
- 특정 위치의 요소를 삭제할 수 있다.

### ArrayList와 Vector의 차이?
- ArrayList
  - initialCapacity를 정한 후, 데이터가 추가되면 용량이 늘어난다.
  - not syncronized. 값을 추가/삭제해야 하지만, thread-safe한 구현이 필요하지 않을 때 사용한다.
- Vector
  - initialCapacity와 capacityIncrement 값을 지정하여, 용량이 찰 때마다 Increment만큼 늘어난다.
  - syncronized. 값을 추가/삭제할 때 동기화되어 멀티쓰레드 환경에서 thread-safe한 구현이 가능하다.

### 👍 List의 장점
- 여러개의 데이터를 한꺼번에 다룰 수 있다.
- 메모리 상에 연속되지 않아도 된다.
- 미리 공간을 확보해놓지 않아도 된다.
- 필요에 따라 데이터가 늘어나거나 줄어든다.

### 👎 List의 단점
- 첫 번째 위치로부터 index로 목표위치를 아려면 한 칸, 한 칸 이동하면서 찾아야 한다.
- Array에 비해 요소를 찾는 속도가 느리다
