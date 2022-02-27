## Optional
Java8부터 Optional<T>클래스를 사용해 NullPointerException(이하 NPE)를 방지할수 있도록 했다.
Optional<T>는 null이 올 수 있는 값을 감싸는 Wrapper 클래스로, 참조하더라도 NPE가 발생하지 않도록 도와준다.
  
Optional 클래스는 아래와 같은 value에 값을 저장하기 때문에 값이 null이더라도 바로 NPE가 발생하지 않으며,
예상치못한 NPE예외를 제공되는 메소드로 간단히 회피할 수 있어 복잡한 조건문 없이도 null값으로 인해 발생하는 예외를 처리할 수 있다.
```
public final class Optional<T> {
  // If non-null, the value; if null, indicates no value is present
  private final T value;
  ...
}
```
  
## Optional 생성하기
- #### 값이 비어있는 경우 - Optional.empty()

빈 Optional 객체는 empty() 메서드를 활용하여 생성할 수 있다.
```
  Optional<String> optional = Optional.empty();
  System.out.println(optional); // Optional.empty
  System.out.println(optional.isPresent()); // false
```
  
- #### 값이 Null이 아닌 경우 - Optional.of()
  
만약 어떤 데이터가 null이 절대 아닌 경우에는 Optional.of()로 아래와 같이 생성할 수 있다.
```
// Optional의 value는 null이 아니다.
Optional<String> optional = Optional.of("MyName");
```
만약 Optional.of()로 Null을 저장하려고 하면 NullPointerException이 발생한다.

- #### 값이 Null일 수도, 아닐 수도 있는 경우 - Optional.ofNullbale()

만약 어떤 데이터가 null이 올 수도 있고 아닐 수도 있는 경우에는 Optional.ofNullbale로 생성할 수 있다.
그리고 이후에 orElse 또는 orElseGet 메소드를 이용해서 값이 없는 경우라도 안전하게 값을 가져올 수 있다.
```
// Optional의 value는 값이 있을 수도 있고 null 일 수도 있다.
Optional<String> optional = Optional.ofNullable(getName());
String name = optional.orElse("anonymous"); // 값이 없다면 "anonymous" 를 리턴
```

## Optional 접근하기
|메서드|기능|
|:--|:--|
|get()|비어있는 Optional 객체를 반환한다.|
|isPresent()|Optional 객체에 저장된 값이 null인지 아닌지 확인한다.|
|orElse()|저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 파라미터의 값을 반환한다.|
|orElseGet()|저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 파라미터의 람다식 결과값을 반환한다.|
|orElseThrow()|저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 파라미터의 예외를 발생시킨다.|
  
## 참고
- [[Java] Optional이란? by 이숭간](https://esoongan.tistory.com/95)
- [[Java] Optional이란? Optional 개념 및 사용법 - (1/2) by 망나니개발자](https://mangkyu.tistory.com/70)
- [[Java] Optional, Optional의 메서드, Optional 사용시 주의사항 by 비비 bibi](https://bibi6666667.tistory.com/286)
