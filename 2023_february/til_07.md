
---

๐ ์๋ก ์๊ฒ๋ ์ฌ์ค ํน์ ์๊ณ  ์๋ ์ฌ์ค์๋ํ ์ง๋ฌธ, ๋ต๋ณ

๐ jpa entity validation nullable==false vs @NotNull

- Nullabled : @Colum์ ์์ฑ ์ค ํ๋๋ก, ๊ธฐ๋ณธ๊ฐ์ true์๋๋ค. ๊ฐ์ false๋ก ์ค์ ํด์ฃผ๋ฉด ํด๋น ํ๋๋ DDL ์์ฑ ์ NOT NULL์ด๋ผ๋ ์กฐ๊ฑด์ด ๋ถ์ ์ฑ๋ก ์์ฑ๋ฉ๋๋ค.

โ ๊ถ๊ธํ ์ ์ด ์์ต๋๋ค. ์์ ๊ฐ์ด nullable==false๋ฅผ ์ค์ ํ๊ฒ ๋๋ค๋ฉด, DB์๋ null์ด ๋ค์ด๊ฐ ์ ์์ง๋ง, Product Code๋ฅผ ์์ฑํ  ๋ null์ property์ ํ ๋นํ  ์ ์์ง ์์๊น?
- ์์ ์ด์  ๋๋ฌธ์ nullable ๋ณด๋ค @NotNull ์ฌ์ฉ์ ์ถ์ฒํ๊ณ  ์๋ค.
- @NotNull์ ์ฌ์ฉํ๋ฉด, DB SQL ์ฟผ๋ฆฌ(JDBC ๋ณํ)๋ฅผ ๋ณด๋ด๊ธฐ ์ ์ ์์ธ๊ฐ ๋ฐ์ํฉ๋๋ค.
- JPA์ Repository ์ธํฐํ์ด์ค๊ฐ ์๋ชป๋ Entity๋ฅผ ์ ์ฅํ  ๋, ConstraintViolationException์ ๋ฐ์์ํต๋๋ค. 

โ ๊ทธ๋ ๋ค๋ฉด @NotNull๋ง๊ณ  @NotEmpty, @NotBlank๋ ๊ฒ์ฆ์ ์ํด ์กด์ฌํ๋๋ฐ ๋ฌด์จ ์ฐจ์ด๊ฐ ์๋์?
- @NotEmpty : **๋ฌธ์์ด**์ null์ด๋ ""๊ฐ ๋ค์ด๊ฐ๋ฉด ์์ธ๋ฅผ ๋ฐ์์ํต๋๋ค. NotNull์ ๋ฌธ์์ด ๋ฒ์  ์์ํธํ
- @NotBlank : **๋ฌธ์์ด**์ null, "", " "์ด ๋ค์ด๊ฐ๋ฉด ์์ธ๋ฅผ ๋ฐ์์ํต๋๋ค. NotEmpty์ ๋ฌธ์์ด ์์ํธํ

โ @NotEmpty @NotEmpty์ด ์์ํธํ์ด๋ผ๋ฉด ์ด ๋ ์ข๋ฅ๋ง ์ฌ์ฉํ๋ฉด ๋๋ ๊ฒ์ด ์๋๊น์?
- NotEmpty๊ณผ NotEmpty๋ DDL ๋ฐ์ ์, NOT NULL option line์ด ์ถ๊ฐ๋์ง ์์ต๋๋ค. ๋ง์ฝ ์ฌ์ฉ์๊ฐ flyway์ ๊ฐ์ ํ์ ๊ด๋ฆฌ ํด๋ก DB๋ฅผ ๊ด๋ฆฌํ๋ค๋ฉด ์๊ด ์๊ฒ ์ง๋ง ๊ทธ๋ ์ง ์๋ค๋ฉด NotNull ์ฌ์ฉํด Library์ ๋์์ ๋ฐ์ ์ ์์ต๋๋ค.

โ ์ @NotEmpty๊ณผ @NotEmpty์ NOT NULL Option์ด ์กด์ฌํ์ง ์๋ ๊ฒ์ผ๊น์?
- ๋ ๊ฒ์ฆ์ **๋ฌธ์์ด**์ ๊ด๋ จํด ๊ฒ์ฆ์ ์งํํ๋ ์ง์ญ์ ์ธ annotation์๋๋ค.
- ๋ฒ์ฉ์ฑ์ ์ง๋ NotNull์ ์ฌ์ฉํ๊ณ  ๋ค๋ฅธ ์ ํ ์กฐ๊ฑด์ ์ถ๊ฐํด Column ์ ํ ์ฌํญ์ ์ถ๊ฐํด ์ฌ์ฉํ  ์ ์์ต๋๋ค.

๐ Instant๋ฅผ ์ฌ์ฉํ๋ ์ด์ 
- ๋ค๋ฅธ Date ๊ด๋ จ Library๋ longํ Unix Timestamp(POSIX, Epoch Time)์ ์ฌ์ฉํฉ๋๋ค. ์ด๋ integer, long์ ์ด์ฉํ ์ ๋ ฌ/์ฐ์ฐ์์ ๋ค๋ฅธ ํ์๋ณด๋ค ๋น ๋ฅธ ์๋๋ฅผ ์๋ํฉ๋๋ค. ํ์ง๋ง, Unix Timestamp๋ **Year 2038 Problem**์ ๊ฐ๊ณ  ์๊ธฐ ๋๋ฌธ์ ๋ค๋ฅธ ํ์์ ์ฌ์ฉํ๋ ๊ฒ์ ๊ถ์ฅํฉ๋๋ค.
- ์ด๋ฅผ ์ํ ํ์์ด Java์ Instant์๋๋ค.
- Instant Type์ ์๋ฐ 1.8 java.time package์ ๋ค์ด๊ฐ์์ผ๋ฉฐ UTC์ ํ์ ๋ผ์ธ์์๋ ์๊ฐ์ผ๋ก, 1970๋ 1์ 1์ผ UTC์ ์ฒซ ๋ฒ์งธ ์๊ฐ ์ดํ์ ํ์ฌ ์๊ฐ๊น์ง์ ๋๋ธ์ด๋ฅผ ๋ํ๋ธ ๊ฐ ์๋๋ค. ๋น์ฆ๋์ค ๋ก์ง, ๋ฐ์ดํฐ ์ ์ฅ ๋ฐ ๋ฐ์ดํฐ ๋ณ๊ฒฝ์ UTC๋ก ์ด๋ฃจ์ด์ ธ์ผํ๋ฏ๋ก ์์ฃผ ์ฌ์ฉํ๊ธฐ์ ํธ๋ฆฌํ ํด๋์ค์๋๋ค.

๐ ๋ก๊ทธ์ธ ์ ์ฌ์ฉํ๋ ์ํธํ๋ฅผ ์งํํ ํ DB์ ์ ์ฌํด์ผ ํฉ๋๋ค. ์ด์ ๋ ํ๋ฌธ(์ค์  ๋น๋ฐ๋ฒํธ)๋ DB์ ์์ด๋ ์์ ํ์ง ์๊ธฐ ๋๋ฌธ์๋๋ค.

โ๏ธ ์ํธํ ์๊ณ ๋ฆฌ์ฆ์ผ๋ก BCrypt๋ฅผ ์ ํํ์ต๋๋ค. ์ด๋ ๋ณตํธํ ๋ถ๊ฐ๋ฅํ ๋จ๋ฐํฅ ์๊ณ ๋ฆฌ์ฆ ์ด๊ธฐ ๋๋ฌธ์๋๋ค. ๋ํ dependency๋ก ์ถ๊ฐํด ์ฌ์ฉํ๊ฒ ๋๋ค๋ฉด ์ถ๊ฐ๋ก ์ํธ๋ฅผ ๋น๊ตํ  ์ ์๋ ๊ธฐ๋ฅ์ ์ ๊ณตํด ์ค๋๋ค.

โ๏ธ ํฌ๋กค๋ง ์ ์ ๊ท์ ์ฌ์ดํธ ์ฐธ๊ณ  (Regexr)[https://regexr.com/]
---
๐ Reference

[javax and jakrata](https://thenicesj.tistory.com/391)

[jakrata validation](https://beanvalidation.org)

[Unix TimeStamp Problem](https://en.wikipedia.org/wiki/Year_2038_problem)