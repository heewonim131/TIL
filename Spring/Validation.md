## Validation
Java에서는 null 값에 대해서 접근하려고 할 때 null pointer exception이 발생하는데,
이러한 부분을 방지하기 위해서 미리 검증하는 과정을 의미한다.
1. 검증해야 할 값이 많은 경우 코드의 길이가 길어진다.
2. 구현에 따라서 달라질 수 있지만 Service Logic과의 분리가 필요하다.
3. 흩어져 있는 경우 어디에서 검증을 하는지 알기 어려우며 재사용의 한계가 있다.
4. 구현에 따라 달라질 수 있지만, 검증 Logic이 변경되는 경우
테스트 코드 등 참조하는 클래스에서 Logic 변경되어야 하는 부분이 발생할 수 있다.

![image](https://user-images.githubusercontent.com/92259017/150723745-16ff0407-c699-4cf1-9ca7-362be234c5cc.png)

### Gradle dependencies
{ implementation("org.springframework.boot:spring-boot-starter-validation") }

### Bean validation spec
https://beanvalidation.org/2.0-jsr380/

![image](https://user-images.githubusercontent.com/92259017/150724070-ec10499c-2126-46bc-a490-843b1ae28b40.png)

<hr>

## Custom Validation
1. AssertTrue / False 어노테이션을 method에 적용하여 Custom Logic 적용 가능<br>
method 이름은 is로 시작해야 한다. 재사용이 불가능하다.<br>
![image](https://user-images.githubusercontent.com/92259017/150724612-9d978504-96c5-489f-b70b-46b4f3e31559.png)

2. ConstrainValidator를 적용하여 재사용이 가능한 Custom Logic 적용 가능<br>
재사용 가능한 어노테이션을 직접 만들어 적용.<br>
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
