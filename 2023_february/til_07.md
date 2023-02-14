
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 jpa entity validation nullable==false vs @NotNull

- Nullabled : @Colum의 속성 중 하나로, 기본값은 true입니다. 값을 false로 설정해주면 해당 필드는 DDL 생성 시 NOT NULL이라는 조건이 붙은 채로 생성됩니다.

❓ 궁금한 점이 있습니다. 위와 같이 nullable==false를 설정하게 된다면, DB에는 null이 들어갈 수 없지만, Product Code를 작성할 때 null을 property에 할당할 수 있지 않을까?
- 위의 이유 때문에 nullable 보다 @NotNull 사용을 추천하고 있다.
- @NotNull을 사용하면, DB SQL 쿼리(JDBC 변환)를 보내기 전에 예외가 발생합니다.
- JPA의 Repository 인터페이스가 잘못된 Entity를 저장할 때, ConstraintViolationException을 발생시킵니다. 

❓ 그렇다면 @NotNull말고 @NotEmpty, @NotBlank도 검증을 위해 존재하는데 무슨 차이가 있나요?
- @NotEmpty : **문자열**에 null이나 ""가 들어가면 예외를 발생시킵니다. NotNull의 문자열 버전 상위호환
- @NotBlank : **문자열**에 null, "", " "이 들어가면 예외를 발생시킵니다. NotEmpty의 문자열 상위호환

❓ @NotEmpty @NotEmpty이 상위호환이라면 이 두 종류만 사용하면 되는 것이 아닐까요?
- NotEmpty과 NotEmpty는 DDL 반영 시, NOT NULL option line이 추가되지 않습니다. 만약 사용자가 flyway와 같은 형상 관리 툴로 DB를 관리한다면 상관 없겠지만 그렇지 않다면 NotNull 사용해 Library의 도움을 받을 수 있습니다.

❓ 왜 @NotEmpty과 @NotEmpty에 NOT NULL Option이 존재하지 않는 것일까요?
- 두 검증은 **문자열**에 관련해 검증을 진행하는 지역적인 annotation입니다.
- 범용성을 지닌 NotNull을 사용하고 다른 제한 조건을 추가해 Column 제한 사항을 추가해 사용할 수 있습니다.

🍏 Instant를 사용하는 이유
- 다른 Date 관련 Library는 long형 Unix Timestamp(POSIX, Epoch Time)을 사용합니다. 이는 integer, long을 이용한 정렬/연산에서 다른 타입보다 빠른 속도를 자랑합니다. 하지만, Unix Timestamp는 **Year 2038 Problem**을 갖고 있기 때문에 다른 타입을 사용하는 것을 권장합니다.
- 이를 위한 타입이 Java의 Instant입니다.
- Instant Type은 자바 1.8 java.time package에 들어가있으며 UTC의 타임 라인에있는 순간으로, 1970년 1월 1일 UTC의 첫 번째 순간 이후의 현재 시간까지의 나노초를 나타낸 값 입니다. 비즈니스 로직, 데이터 저장 및 데이터 변경은 UTC로 이루어져야하므로 자주 사용하기에 편리한 클래스입니다.

🍏 로그인 시 사용하는 암호화를 진행한 후 DB에 적재해야 합니다. 이유는 평문(실제 비밀번호)는 DB에 있어도 안전하지 않기 때문입니다.

❗️ 암호화 알고리즘으로 BCrypt를 선택했습니다. 이는 복호화 불가능한 단반향 알고리즘 이기 때문입니다. 또한 dependency로 추가해 사용하게 된다면 추가로 암호를 비교할 수 있는 기능을 제공해 줍니다.

✒️ 크롤링 시 정규식 사이트 참고 (Regexr)[https://regexr.com/]
---
📚 Reference

[javax and jakrata](https://thenicesj.tistory.com/391)

[jakrata validation](https://beanvalidation.org)

[Unix TimeStamp Problem](https://en.wikipedia.org/wiki/Year_2038_problem)