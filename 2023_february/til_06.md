
π μλ‘ μκ²λ μ¬μ€ νΉμ μκ³  μλ μ¬μ€μλν μ§λ¬Έ, λ΅λ³

β InnoDBμμ PKλ₯Ό λ€λ₯Έ Engineμ λΉν΄ κ°μ‘°νκ³  μλ€ μ΄μ λ λ¬΄μμΌκΉ?
β Insert, Update, Deleteμ μ±λ₯μ ν¬μνκ³  Indexλ₯Ό μ¬μ©ν΄ μ‘°νμ μ±λ₯μ λμ΄λ κ²μ΄ λͺ©νμ΄κΈ° λλ¬Έμλλ€.
β Mysqlμ PKλ₯Ό μ€μ νμ§ μμλ μλμΌλ‘ ν΄λ¬μ€ν°λ§ μΈλ±μ€λ₯Ό μ κ³΅ν©λλ€. νμ§λ§ Mysqlμ΄ μλμΌλ‘ μ κ³΅νλ ν΄λ¬μ€ν°λ§ μΈλ±μ€λ μ¬μ©μκ° λ³Ό μ μμ΄ PKλ₯Ό μ€μ ν΄ μ¬μ©νλ κ²μ΄ μ’μ΅λλ€.

β ν΄λ¬μ€ν°λ§ μΈλ±μ€λ λ¬΄μμΈκ°μ?
β ν΄λ¬μ€ν°λ§μ΄λ μ¬λ¬ κ°λ₯Ό νλλ‘ λ¬Άλλ€λ μλ―Έλ‘ μ£Όλ‘ μ¬μ©λ©λλ€. Mysql μλ²μμ ν΄λ¬μ€ν°λ§μ νμ΄λΈμ λ μ½λλ₯Ό λΉμ·ν κ²(PK κΈ°μ€)λ€λΌλ¦¬ λ¬Άμ΄μ μ μ₯νλ ννλ‘ κ΅¬νλ©λλ€.
μ΄λ λΉμ·ν κ°λ€μ λμμ μ‘°ννλ κ²½μ°κ° λ§λ€λ μ μ μ°©μν κ²μλλ€.

β ν΄λ¬μ€ν°λ§ μΈλ±μ€λ InnoDB μ€ν λ¦¬μ§ μμ§μμλ§ μ§μνλ©°, λλ¨Έμ§ μ€ν λ¦¬μ§ μμ§μμλ μ§μλμ§ μμ΅λλ€.

β λ€μ λ§ν΄, λΉμ·ν λ μ½λλΌλ¦¬ λ¬Άμ΄μ μ μ₯νλ κ²μ ν΄λ¬μ€ν°λ§ μΈλ±μ€λΌκ³  ννν©λλ€.

β μ κΈκ³Ό νΈλμ­μμ μ°¨μ΄λ λ¬΄μμΈκ°μ?

β μ κΈκ³Ό νΈλμ­μμ μλ‘ λΉμ·ν κ°λ κ°μ§λ§ λ€λ¦λλ€.

- μ κΈ : μ κΈμ λμμ±μ μ μ΄νκΈ° μν κΈ°λ₯μλλ€.
- νΈλμ­μ : νΈλμ­μμ λ°μ΄ν°μ μ ν©μ±μ λ³΄μ₯νκΈ° μν κΈ°λ₯μλλ€.

β μ κΈμ μ¬λ¬ μ»€λ₯μμμ λμμ λμΌν μμμ μμ²­ν  κ²½μ° μμλλ‘ ν μμ μλ νλμ μ»€λ₯μλ§ λ³κ²½ν  μ μκ² ν΄μ£Όλ μ­ν μ ν©λλ€.

β κ²©λ¦¬ μμ€μ΄λΌλ κ²μ νλμ νΈλμ­μ λ΄μμ λλ μ¬λ¬ νΈλμ­μ κ°μ μμ λ΄μ©μ μ΄λ»κ² κ³΅μ νκ³  μ°¨λ¨ν  κ²μΈμ§λ₯Ό κ²°μ νλ λ λ²¨μλλ€.

β Mysql AEC, DESCμ μ±λ₯ μ°¨μ΄λ μ κ·Έλ¦¬κ³  μ΄λμμ λ°μνλ κ²μΌκΉ?

β 

β λ³λ ¬ μ²λ¦¬μ© μ€λ λ κ°μλ₯Ό μλ¬΄λ¦¬ λλ¦¬λλΌλ μλ²μ μ₯μ°©λ CPUμ μ½μ΄ κ°μλ₯Ό λμ΄μλ κ²½μ°μλ μ€νλ € μ±λ₯μ΄ λ¨μ΄μ§ μ μλ μ΄μ λ λ¬΄μμΈκ°μ?

β μ λ΅μ Context Switchingμ μμ΅λλ€. μ΄ λ  Overheadκ° λ°μν΄ μ±λ₯μ΄ λ¨μ΄μ§λ κ²μΈλ° Overheadλ μ΄λ€ μ²λ¦¬λ₯Ό νκΈ° μν΄ λ€μ΄κ°λ κ°μ μ μΈ μ²λ¦¬ μκ°, λ©λͺ¨λ¦¬ λ±μ λ»ν©λλ€.

β μμ²­μ΄ λ§μμ§λ€λ©΄ κ·Έλ§νΌ λ¬Έλ§₯ κ΅νμ΄ μ¦μμ§λλ€. μ΄λ Overheadλ₯Ό μ΄λνκ²λλ©° Process μ±λ₯μ λ?μΆ₯λλ€.

selled interface

kakao tech blog aec desc μ±λ₯ μ°¨μ΄