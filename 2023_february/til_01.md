
---

๐ ํ๋ก์ ํธ ๊ด๋ จ
โ xml File์ Entity์ ๋งคํ๋์ด ์๋ ResultMap์ ๊ฑท์ด๋ด๊ณ  Repository์ Mybatis Dao ์ฌ์ด์ Model Mapper๋ฅผ ๋์ต๋๋ค.
โ Model Mapper๋ฅผ ๋์ํ๊ฒ ๋ ์ด์ ๋ Entity์ ์์กด์ฑ์ด ์๋ xml ํ์ผ์์ ๋ ์ฌ์ด์ Model Mapper๋ฅผ ๋ผ์๋ฃ์ด xml file์ ๊ฐ๋์ฑ์ ๋์ด๊ณ  ํ๋ก๋ํธ ์ฝ๋ ๋ ๋ฒจ์์  ๋น์ง๋์ค์ ๋ ์ง์คํ  ์ ์๊ธฐ ๋๋ฌธ์๋๋ค.
โ HttpClient๋ฅผ ์ฌ์ฉํด ๋ค๋ฅธ ํจํค์ง์ ์์ฒญ์ ๋ณด๋ด Package ๊ฐ ํต์ ์ ๋ง๋ค์์ต๋๋ค.

โ ์๋ ์ฌ์ง์ ๋ณด๋ฉด ๊ทธ ์ฐจ์ด๋ฅผ ๋ ํ์คํ๊ฒ ์ ์ ์์ต๋๋ค.

<Entity์ Mybatis xml File์ด ๊ฐํ๊ฒ ๋งบํ ๊ฒฝ์ฐ>
![EntityResultMappingInXmlFile](image/EntityResultMappingInXmlFile.png)

<์ง์  ์ฟผ๋ฆฌ๊ฐ ์์ฑ๋๋ ๋ถ๋ถ>
![EntityResultMappingQuerySection](image/EntityResultMappingQuerySection.png)

<Model Mapper ๋ณ๊ฒฝ ํ ๊ฒฐ๊ณผ>
![ModelMapperResult](image/ModelMapperResult.png)

โ ์ ๊ณผ์ ์ ๊ฑฐ์น ๊ฒฐ๊ณผ ๋์ฑ ๊น๋ํด์ง ์ฝ๋๋ฅผ ์ป์ ์ ์์์ต๋๋ค.

๐ ์๋ก ์๊ฒ๋ ์ฌ์ค ํน์ ์๊ณ  ์๋ ์ฌ์ค์๋ํ ์ง๋ฌธ, ๋ต๋ณ

๐ DAO, MapperModel, MapperDto
โ Mybatis์์ DAO๋ @Mapping Annotaion์ ๊ฐ๊ณ  ์๋ ๊ฐ์ฒด๊ฐ ๋ด๋นํฉ๋๋ค. ํด๋น ๊ฐ์ฒด๋ Repository์ DB์ฌ์ด์ ์กด์ฌํ๋ฉฐ ๊ณ์ธต ์ฌ์ด ๋ถ๋ฆฌ๋ฅผ ๋์์ค๋๋ค.

โ MapperModel์ Entity์ Mapper ์ฌ์ด์ ์กด์ฌํ๋ฉฐ Entity๊ฐ ๊ฐ๊ณ  ์๋ Property๋ฅผ Flatํ๊ฒ ๋ง๋ค์ด์ค๋๋ค. ์ด๋ DB์ Data๋ฅผ ์ ์ฌํ  ๋ ์ค์ํ๊ฒ ์์ฉํฉ๋๋ค. DB์ ์ ์ฌ๋  ๋ DB๋ ์ฌ์ฉ์๊ฐ ์ ์ํ ๋ฐ์ดํฐ๋ฅผ ์์ง ๋ชปํ๊ณ  Manageํ  ์ ์๋ ๋ฐ์ดํฐ๋ง์ ์ฒ๋ฆฌํ  ์ ์์ต๋๋ค.

โ MapperDto๋ DB์์ ์ฝ์ Query๋ฅผ ๋ฐํ์ผ๋ก ๊ฐ์ ธ์ค๋ ๋ฐ์ดํฐ๋ค์ ๋ด๋ ์ญํ ์ ์ํํฉ๋๋ค. DB ์์ ์ด ๋ค๋ฃฐ ์ ์๋ ๋ฐ์ดํฐ๋ง์ ์ฌ์ฉํ  ์ ์์์ผ๋ก MapperDto ํ๋ ํ์์ ๊ธฐ๋ณธ ํ์์ ๊ฒฝ์ฐ๊ฐ ๋ง์ต๋๋ค.

๐ Java ์ธํฐํ์ด์ค ์ฌ์ฉ์ ๊ดํ ์๊ฐ
โ ์ง๋ฌธ์ ๋ฐ์์ต๋๋ค. DB์์ ๋ฐ์ํ๋ Exception๋ DIP๋ฅผ ํตํด ์์ธ๋ฅผ ๋์ง๋ ๊ฒ์ ์์๋์?
โ ์ฌํ DB์์ ๋์ง๋ ์์ธ๋ฅผ IDE์์ ์๋์ผ๋ก ๋์์ค์ ์ด๋ฐ ์๊ฐ์ ํด๋ณธ ์ ์ด ์์์ต๋๋ค. ์ด๋ฅผ ์์๋ณด๊ธฐ ์ํด DIP๋ฅผ ์ด๋ฃจ๊ธฐ์ํด ์ด๋ค ๋ฐฉ์์ ์ฌ์ฉํ๋์ง ์ ์๊ฐ ํ์ํ์ต๋๋ค.
โ DIP๋ฅผ ์ด๋ฃจ๊ธฐ ์ํด Interface๋ผ๋ ๊ท์ฝ์ ์ ์ํ  ์ ์๋ ๋ถ๋ถ์ ๋ง๋ค์์ต๋๋ค.

  โ ๊ทธ๋ ๋ค๋ฉด Interface๊ฐ ์๋ค๋ฉด ์ด๋ค ์ผ์ด ๋ฐ์ํ ๊น์?
  โ Interface๊ฐ ์์ ๋๋ฅผ ์๊ฐํด๋ด์๋ค. ์ด๋ฏธ์ง์์ ์ ์ ์๋ฏ์ด ๊ณ ์์ค์ A ํด๋์ค์์ ์ ์์ค์ B, C ํด๋์ค์์ํด A์ ๋ณ๊ฒฝ์ ์ฌํ๊ฐ ํฝ๋๋ค.
  ![bClass_Parameter_image](image/bClass.png)
  ![cClass_Parameter_image](image/cClass.png)

  Tip) ๊ณ ์์ค์ ๊ฐ์ฒด์ ์ ์์ค์ ๊ฐ์ฒด๋ ์ด๋ ํ ๊ธฐ์ค์ผ๋ก ๋๋๋์?
  * ๊ณ ์์ค์ ๊ฐ์ฒด์ ์ ์์ค์ ๊ฐ์ฒด๋ ์๋์ ์๋๋ค.
  * ์ด ๋ ๊ธฐ์ค์ ๋๋๋ ์กฐ๊ฑด์ ์ฒซ์งธ, ์์ถ๋ ฅ๊ณผ์ ๊ฑฐ๋ฆฌ๊ฐ ์ผ๋ง๋ ๋จ์ด์ ธ ์๋๋ ๊ฒ์ด๊ณ  ๋์งธ๋ ํต์ฌ ์ ์ฑ์ ์ผ๋ง๋ ๋ ๋ง์ด ์์ ํ๋๊ฐ์๋๋ค.
  โ Interface๋ฅผ ์ฌ์ฉํ์ง ์๋๋ค๋ฉด ๋ณ๊ฒฝ์ ์ฌํ๊ฐ ์ต์ํ๋์ด์ผ ํ๋ **๊ณ ์์ค**์์ ์ ์ฑ์ด ๋ฐ๋ ๋๋ง๋ค ๋ง์ ๋ณ๊ฒฝ ์ฌํญ์ด ๋ฐ์ํฉ๋๋ค.

  โ Interface๋ฅผ ์ฌ์ฉํ๋ฉด ์ด๋ป๊ฒ ๋๋์?
  ![Interface_์ ์ฉ](image/interfaceDefine.png)
  โ ์์ ๊ฐ์ด ์ ์ฉํ๊ฒ ๋๋ค๋ฉด ๊ณ ์์ค์ ๊ฐ์ฒด๊ฐ ์ ์์ค์ ๊ฐ์ฒด๋ฅผ ์ฌ์ฉํ๋ค ํ๋ค ์ํฅ์ ๋ฐ์ง ์์ต๋๋ค.
  ![Interface_์ ์ฉ_ํ_๋ชจ์ต](image/implementationInterface.png)

  โ ๋ค์ ๋์์์ DB์ ๊ทธ DB๋ฅผ ์ฌ์ฉํ๊ณ  ์๋ ํ๋ก์ ํธ์์ ๊ด๊ณ๋ฅผ ์ดํด๋ณด๋ฉด DB์์ ์์ธ๊ฐ ๋ฐ์ํ  ๋(Ex, DB Syntax Exception), DB์์ ๋์ง ์์ธ๋ฅผ ๋ฐ์์ ์์ธ๋ฅผ ํฐํธ๋ ค์ค๋๋ค.

๐ Path Variable๊ณผ Query Parameter๋ ์ธ์  ์ฌ์ฉํด์ผ ํ ๊น?
โ ๋ง์ฝ ์ด๋ค resource๋ฅผ ์๋ณํ๊ณ  ์ถ์ผ๋ฉด Path Variable์ ์ฌ์ฉํ๊ณ ,์ ๋ ฌ์ด๋ ํํฐ๋ง์ ํ๋ค๋ฉด Query Parameter๋ฅผ ์ฌ์ฉํ๋ ๊ฒ์ด Best Practice์ด๋ค.


๐ Effective Java
* ์์ธ๋ ์ง์ง ์์ธ ์ํฉ์๋ง ์ฌ์ฉํ๋ผ
* ๋ณต๊ตฌํ  ์ ์๋ ์ํฉ์๋ ๊ฒ์ฌ ์์ธ๋ฅผ, ํ๋ก๊ทธ๋๋ฐ ์ค๋ฅ์๋ ๋ฐํ์ ์์ธ๋ฅผ ์ฌ์ฉํ๋ผ
* ํ์ ์๋ ๊ฒ์ฌ ์์ธ ์ฌ์ฉ์ ํผํ๋ผ
* ํ์ค ์์ธ๋ฅผ ์ฌ์ฉํ๋ผ
* ์ถ์ํ ์์ค์ ๋ง๋ ์์ธ๋ฅผ ๋์ง๋ผ
* ๋ฉ์๋๊ฐ ๋์ง๋ ๋ชจ๋  ์์ธ๋ฅผ ๋ฌธ์ํํ๋ผ
* ์์ธ์ ์์ธ ๋ฉ์ธ์ง์ ์คํจ ๊ด๋ จ ์ ๋ณด๋ฅผ ๋ด์ผ๋ผ
* ๊ฐ๋ฅํ ํ ์คํจ ์์์ ์ผ๋ก ๋ง๋ค๋ผ
* ์์ธ๋ฅผ ๋ฌด์ํ์ง ๋ง๋ผ
