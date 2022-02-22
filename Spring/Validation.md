## Validation 이란
Java에서는 null 값에 대해서 접근하려고 할 때 null pointer exception이 발생하는데,
이러한 부분을 방지하기 위해서 미리 검증하는 과정을 의미한다.
- 검증해야 할 값이 많은 경우 코드의 길이가 길어진다.
- 구현에 따라서 달라질 수 있지만 Service Logic과의 분리가 필요하다.
- 흩어져 있는 경우 어디에서 검증을 하는지 알기 어려우며 재사용의 한계가 있다.
- 검증 Logic이 변경되는 경우 테스트 코드 등 참조 클래스에서 Logic이 변경되어야 하는 부분이 발생할 수 있다.

### Validation Annotations
|Annotation|의미|
|:--|:--|
|@Size|문자 길이 측정|
|@NotNull|null 불가|
|@NotEmpty|null, "" 불가|
|@NotBlank|null, "" 불가|
|@Past|과거 날짜|
|@PastOrPresent|오늘이거나 과거 날짜|
|@Future|미래 날짜|
|@FutureOrPresent|오늘이거나 미래 날짜|
|@Pattern|정규식 적용|
|@Max|최대값|
|@Min|최소값|
|@AssertTrue/False|별도 Logic 적용|
|@Valid|해당 Object Validation 실행|

### Gradle dependencies
```
dependencies {
  implementation 'org.springframework.boot:spring-boot-starter-validation'
  ...
}
```

## Validation 여러가지 기능
- ### Service나 Bean에서 사용하기 위해서는 '@Validated'와 '@Valid'를 추가해야 한다.
```
@Validated // 여기에 추가
@Service
public class ContactService {
    public void createContact(@Valid CreateContact createContact) { // '@Valid'가 설정된 메서드가 호출될 때 유효성 검사를 진행한다.
        // Do Something
    }
}
```

- ### Controller는 '@Validated'가 필요 없다. 검사를 진행할 곳에 '@Valid'를 추가하면 된다.
```
@PostMapping("/contacts")
public Response createContact(@Valid CreateContact createContact) { // 메서드 호출 시 유효성 검사 진행
    return Response
        .builder()
        .header(Header
            .builder()
            .isSuccessful(true)
            .resultCode(0)
            .resultMessage("success")
            .build())
        .build();
}
```
주의할 점은 데이터 유효성 검사를 진행할 때 검사가 중복으로 실행되지 않도록 해야 한다는 것이다.
같은 데이터 유효성 검사가 여러 번 실행될 경우 애플리케이션 성능에 영향을 미칠 수 있다.

- ### 컨테이너(Container)의 요소(Element)에 대한 유효성 검사
Bean Validation 2.0부터 컨테이너의 요소에 대해 유효성 검사가 가능해졌다. 아래와 같이 제약을 정의할 수 있다.
```
public class DeleteContacts {
    @Min(1)
    private Collection<@Length(max = 64) @NotBlank String> uids;
}
```

- ### 사용자 정의 검증 (Custom Validation)
Bean Validation에서는 필요한 제약을 직접 정의해서 사용할 수 있도록 기능을 제공한다. 
1. AssertTrue / False 어노테이션을 method에 적용하여 Custom Logic을 적용할 수 있다.<br>
method 이름은 is로 시작해야 하고, 재사용이 불가능하다.

![image](https://user-images.githubusercontent.com/92259017/150724612-9d978504-96c5-489f-b70b-46b4f3e31559.png)

2. ConstrainValidator를 적용하여 재사용이 가능한 Custom Logic을 적용할 수 있다.<br>
재사용 가능한 어노테이션을 직접 만들어 적용하는 예시이다.<br>
```@YearMonth```
```
package com.example.validation.validator;

import com.example.validation.annotation.YearMonth;

import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

public class YearMonthValidator implements ConstraintValidator<YearMonth, String> {

    private String pattern;

    @Override
    public void initialize(YearMonth constraintAnnotation) {
        this.pattern = constraintAnnotation.pattern();
    }

    @Override
    public boolean isValid(String value, ConstraintValidatorContext context) {

        // yyyyMM
        try{
            LocalDate localDate = LocalDate.parse(value+"01" , DateTimeFormatter.ofPattern(this.pattern));
        }catch (Exception e){
            return false;
        }


        return true;
    }
}
```
```
package com.example.validation.annotation;

import com.example.validation.validator.YearMonthValidator;

import javax.validation.Constraint;
import javax.validation.Payload;
import java.lang.annotation.Retention;
import java.lang.annotation.Target;

import static java.lang.annotation.ElementType.*;
import static java.lang.annotation.ElementType.TYPE_USE;
import static java.lang.annotation.RetentionPolicy.RUNTIME;

@Constraint(validatedBy = {YearMonthValidator.class})
@Target({ METHOD, FIELD, ANNOTATION_TYPE, CONSTRUCTOR, PARAMETER, TYPE_USE })
@Retention(RUNTIME)
public @interface YearMonth {

    String message() default "yyyyMM 형식에 맞지 않습니다.";

    Class<?>[] groups() default { };

    Class<? extends Payload>[] payload() default { };

    String pattern() default "yyyyMMdd";
}
```

## 참고
- [Validation 어디까지 해봤니? by NHN 신진호 개발자님](https://meetup.toast.com/posts/223)
