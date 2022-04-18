## Map
Map은 <Key, Value> 한 쌍의 데이터를 다루는 자료구조로, 빠른 데이터 접근과 유연한 확장이 가능하다.  
Map 인터페이스를 구현한 클래스로는 Hashtable, Hashmap 등이 있다.  
```
Map<String, Integer> map = new Hashtable<>();
Map<String, Integer> map = new Hashtable<>();
...
```
- Hashtable
  - synchronized.
  - 동기화가 필요할 때 사용한다.
- Hashmap
  - not synchronized.
  - thread-safe한 구현이 필요하지 않다면 Hashmap 사용을 권장한다.
- ConcurrentHashmap
  - synchronized + high concurrency.
  - 동기화를 사용하면서도 더 빠른 퍼포먼스를 보여야 할 때 유리하다.

<br>

### Map의 데이터 접근
![image](https://user-images.githubusercontent.com/92259017/163751259-427fd214-069b-4fdb-a5b0-cc5f69388ebc.png)

- `put(key, value)` : 데이터 추가
- `get(key)` : 데이터 읽기
- `remove(key)` : 데이터 삭제

<br>

## Set
```
Set<Integer> set = new HashSet<>();
Set<Integer> set = new TreeSet<>();
...
```
- 선형 데이터 구조 + 탐색 알고리즘
- 중복된 값을 허용하지 않는다.
- 순서를 보장하지 않는다.
