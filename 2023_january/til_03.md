
---

๐ ํฐ ์์ ๋ฐ์ดํฐ๋ฅผ ํ๊บผ๋ฒ์ ์ ์ฌํด๋ณธ ์ ์ด ์์ด ๋ค๋์ ๋ฐ์ดํฐ๊ฐ ์๋ ํ ๊ฑด์ ๋ฐ์ดํฐ๋ก Flow๋ฅผ ์ก์ ํ ํฐ ๋ฐ์ดํฐ๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ์ ์ ํํ์ต๋๋ค.

๐ย ์ฝ๋ ์์ฑ ์ Domain์ ์ฐ์ ์ ์ผ๋ก ์์ฑํ๋ ๊ฒ์ด ์๋ Presentation ๊ณ์ธต ๋จผ์  ์์ฑํ๊ธฐ ์์ํ์ต๋๋ค.

โ ์ Domain์ ๋จผ์  ์์ฑํ์ง ์๊ณ  Presentation(Controller)๋ถํฐ ์ฝ๋๋ฅผ ์์ฑํ๋์?

โ Controller ๋ถํฐ ์์ฑํ ์ด์ ๋ ํ์๋ฅผ ๋จผ์  ๊ฒฐ์ ํ๊ธฐ ์ํจ์๋๋ค. ์ฌ๊ธฐ์ ์ด์ผ๊ธฐํ๋ ํ์๋ ๊ฐ์ฒด๊ฐ ๊ฐ๋ ๋ฉ์๋๋ฅผ ์ด์ผ๊ธฐํ๊ธฐ๋ณด๋จ ํ๋ก์ ํธ์์ ๋ฐ์ ์์ฒญ์ด ์ํ๋๋ ํ์๋ฅผ ๋ปํฉ๋๋ค.

โ ์ด๋ฅผ ํตํด ์ป์ ์ ์๋ ์ฅ์ ์ ๋ฐ์ดํฐ ์ค์ฌ์ ์ผ๋ก ์๊ฐํ์ง ์๊ฒ๋๊ณ  ์ ์ฐํ๊ฒ Domain์ ์ํ(property)๋ฅผ ๊ฐ์ ธ๊ฐ ์ ์์ต๋๋ค.

โ ๏ธย ๋ฌธ์ ๊ฐ ๋ฐ์ํ์ต๋๋ค. Log๋ฅผ ํตํด ๊ฐ์ ์ฐ์ด๋ณด๋ ์ค ๊ฐ์ด ๋๋ฌํ์ง ์๋ ๊ฒ์ ๋ฐ๊ฒฌํ์ต๋๋ค. InMemory๋ก ์งํ๋๋ ํ๋ก์ ํธ์์ ๊ฐ์ด ๋ค์ด๊ฐ ์๋ณ์ ๊ฐ์ด ๋ค์ด๊ฐ๋ ๊ฒ๊น์ง ์ ์์ ์ผ๋ก ๋์ํ๋ ๊ฒ์ ํ์ธํ๋๋ฐ ์ถ์ ํด๋ณด๋ @RequestBody๋ฅผ ํตํด DTO Request๊ฐ ๋ค์ด์ฌ ๋ ๊ฐ์ ์ฝ์ด์ค์ง ๋ชปํ๋ ๊ฒ์ด์์ต๋๋ค.

โ ์๋์ ๊ฐ์ด ๋ฌธ์ ๊ฐ ๋ฐ์ํฉ๋๋ค.

![๋ฐ์ดํฐ_์ค๋ฅ_์ฌ์ง](image/DataNullImage.png)

โ ์ฌํ @RequestBody ๋ด๋ถ ๋์์ ์๊ฐํด๋ณด์ง ์์ ์ฑ ์ฌ์ฉํด ๋ฐ์ํ ๋ฌธ์ ์๋๋ค.

โRequestBody ๋ด๋ถ์ ์ด๋ค ๊ฒ๋ค์ด ์๊ธธ๋ Json Type Request DTO์ ๊ฐ์ ์ฝ์ด์ค๋ ๊ฒ์ธ๊ฐ์?

> Annotation indicating a method parameter should be bound to the body of the web request. The body of the request is passed through anย [HttpMessageConverter]
ย to resolve the method argument depending on the content type of the request. Optionally, automatic validation can be applied by annotating the argument withย `@Valid`
> 

โ ๊ณต์ ๋ฌธ์์์ ๋์จ ์ด์ผ๊ธฐ๋ฅผ ๋ณด๋ฉด ์ปจํ์ธ ์ ์ ํ์ ๋ฐ๋ผ HttpMessageConverter๋ฅผ ํตํด ์ ๋ฌ์ด๋๋ค๊ณ  ๋์์์ต๋๋ค.

โ๊ทธ๋ฐ๋ฐ RequestBody๋ File type์ @interface์๋๋ค. ์ด๋ค ๋ฐฉ์์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๋๊ฑด๊ฐ์?

![Untitled](image/RequestBodyAnnotationImage.png)

โ Annotation์ ์์์ ํ  ์ ์๊ณ  ํ๋ก๊ทธ๋จ์๊ฒ ์ถ๊ฐ ์ ๋ณด๋ฅผ ์ ๊ณตํ๋ ๋ฉํ ๋ฐ์ดํฐ๋ฅผ ์ํด์ ์ฌ์ฉ๋ฉ๋๋ค.

โ์ด๋ค ๋ฐฉ์์ผ๋ก Annotation์ ์ฝ์ด์ค๋ ๊ฒ์ผ๊น์?

โ ์ด๋ฅผ ์๊ธฐ ์ํด์  Spring mvc ๊ตฌ์กฐ๋ฅผ ์์์ผ ํฉ๋๋ค.

- Request๊ฐ ๋ค์ด์ค๋ฉด HandlerMapping์ ํตํด ์ฌ์ฉ์์ ์์ฒญ๊ณผ ํด๋น ์์ฒญ์ ์ด๋ฆฌํ๋ Hanller๋ฅผ ๋งคํํฉ๋๋ค.
- ๋ค์ HandlerMethodArgumentResolver๋ฅผ ์ฌ์ฉํด Controller์ Argument(Parameter)์ ์ง์ ๋ ๋ณ์๋ค์ Annotation์ด๋ ๊ฐ์ฒด์ Type์ ๋ฐ๋ผ์ Resolver๋ฅผ ๊ฑฐ์นฉ๋๋ค.

![Resolver_supportsParam](image/SupportParamImage.png)

โ HandlerArgumentResolver๋ฅผ ์์ํ `RequestResponseBodyMethodProcessor` ๋ฅผ ๋ณด๋ฉด @RequestBody๋ฅผ ํ์ธํ๋ ๊ฒ์ ๋ณผ ์ ์์ต๋๋ค.

โ @RequestBody๋ฅผ ์ฌ์ฉํ ๊ฒ์ด ํ์ธ์ด ๋๋ค๋ฉด read Or write๋ก ๋์ด๊ฐ๊ฒ ๋ฉ๋๋ค.

![JacksonConverter_Class](image/JacksonConverterImage.png)

โ Content-type์ด Json์ธ ๊ฒ์ ์ ํ Jackson Converter๋ฅผ ํตํด Json Data๊ฐ ์ง๋ ฌํ๋ฉ๋๋ค. ์ด ๋ ์ฌ์ฉ๋๋ ๊ฒ์ด ObjectMapper์๋๋ค.

๐ย ObjectMapper๊ฐ Json type ๋ฐ์ดํฐ๋ฅผ ๋งค์นํ๋ ๋ฐฉ์

![ObjectMapper_์๊ฐ](image/ObjectMapperImage.png)

๐ย ObjectMapper๋ฅผ ํตํด Json file์ ์ง๋ ฌํ๋ฅผ ํ ๊ฒฝ์ฐ ๊ฒฐ๊ณผ

โ ์ด๋ฅผ ๋ณด๋ฉด ๋ฐ์ดํฐ๊ฐ ์ ๋ค์ด์จ ๊ฒ์ ๋ณผ ์ ์์ต๋๋ค.

![๋ฌธ์ _ํด๊ฒฐ](image/DataSolveImage.png)

โย ์ง๋ ฌํ ๊ณผ์ ์ด ํ์ํ  ๋, Getter์ ๊ธฐ๋ณธ ์์ฑ์๋ฅผ ๋ถ์ฌ ์ฌ์ฉํ์

---

๐ Reference

[RequestBody (Spring Framework 6.0.3 API)](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/bind/annotation/RequestBody.html)

[Jackson ObjectMapper](https://jenkov.com/tutorials/java-json/jackson-objectmapper.html#how-jackson-objectmapper-matches-json-fields-to-java-fields)

[[Spring] - @RequestBody ์ด๋ธํ์ด์์ ๋์๋ฐฉ์](https://kim-jong-hyun.tistory.com/60)