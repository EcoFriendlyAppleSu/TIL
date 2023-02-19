
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 스프링 부트가 제공하는 테스트 Annotation들은 **실제 스프링 컨텍스트를 사용해 빈들을 등록**한다. 그러므로 @Autowired로 등록된 빈을 주입받을 수 있다.

🍏 JPA는 EntityManager가 EntityContext Container를 관리합니다. 이 때, 관리 대상은 인스턴스된 각자의 객체입니다.

🍏 JPA에서 연관관계를 맺지 않는다면 JdbcCode로 변경되는 과정에 타입을 찾지 못해 "Could not determine recommended JdbcType for XXX" 예외가 발생한다.

→ 이는 기본 타입이 아닌 사용자 지정 참조 타입을 JPA는 알지 못하기 때문이며 연관관계를 맺어줘 JPA에게 알려줘야한다.