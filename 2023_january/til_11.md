
---

🍎 프로젝트 관련
→ 어제 고민했던 변경의 여파를 최소화 할 수 있는 방법으로 테스트 코드를 작성하는 것을 생각했습니다. 지금껏 테스트 코드를 작성할 때 큰 의미 없이 작성했지만 요구사항이 변경되고 그로 인해 변경이 어디에서 발생하는지 파악할 수 없었습니다. 이제야 테스트 코드의 필요성을 느꼈습니다.
→ 테스트 코드 작성의 연장선으로 총 데이터를 DB로 밀어 넣을 때 Edge Case들이 발생한 것을 체크하지 못해 시간이 걸렸습니다. 이 부분에서 리팩토링이 필요합니다.

후에 해결해야 할 것들
🍏 webclient와 urlConnection을 사용할 때 x,y 값이 다르게 들어오는 것에 대해 확인해야 합니다.
🍏 x, y 좌표를 입력할 때 DB에 온전한 값이 들어가는게 아닌 소숫점 세번째 자리까지 들어가는 것을 해결해야 합니다.
🍏 Client entity에서 자신의 위치 기반으로 가까운 수영장을 보여주는 것을 구현해야 합니다.

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍎 Test Code의 종류

- 단위 테스트 : 단위 테스트는 응용 프로그램에서 테스트 가능한 가장 작은 소프트웨어를 실행하여 예상대로 동작하는지 확인하는 테스트입니다.
- 통합 테스트 : 통합 테스트는 단위 테스트보다 더 큰 동작을 달성하기 위해 여러 모듈들을 모아 이들이 의도대로 협력하는지 확인하는 테스트입니다.
- 인수 테스트 : 인수 테스트는 사용자 스토리(시나리오)에 맞춰 수행하는 테스트입니다.

🍏 단위 테스트

→ 단위 테스트에서 테스트 대상 단위의 크기는 엄격하게 정해져 있지 않습니다. 하지만, 일반적으로 클래스 또는 메소드 수준으로 정해진다. 단위의 크기가 작을수록 복잡성이 낮아지고 단위 테스트를 활용하여 동작을 표현하기 더 쉬워진다.

→ 즉, 테스트 대상 단위의 크기를 작게 설정해서 단위 테스트를 최대한 간단하고 디버깅하기 쉽게 작성해야 한다.

🍏 통합 테스트

→ 통합 테스트는 단위 테스트와 달리 개발자가 변경할 수 없는 부분(ex. 외부 라이브러리)까지 묶어 검증할 때 사용한다. 이는 DB에 접근하거나 전체 코드와 다양한 환경이 제대로 작동하는지 확인하는데 필요한 모든 작업을 수행할 수 있다. 그러나, 통합 테스트가 응용 프로그램이 완전하게 작동하는 걸 무조건 증명하지는 않는다.

→ 통합 테스트의 장점은 **단위 테스트에서 발견하기 어려운 버그를 찾을 수 있다는 점이다.** 예를 들어, 통합 테스트에서는 환경 버그(ex. 싱글 코어 CPU에서는 잘 실행되나 쿼드 코어 CPU에서는 잘 실행되지 않음)이 발생할 수 있다.

🍏 인수 테스트

→ 앞선 두 테스트들과 달리 비즈니스 쪽에 초점을 둔다. 프로젝트에 참여하는 사람들(ex. 기획자, 클라이언트 대표, 개발자 등)이 토의해서 시나리오를 만들고, 개발자는 이에 의거해서 코드를 작성한다. 개발자가 직접 시나리오를 제작할 수도 있지만, `다른 의사소통집단으로부터 시나리오를 받아(인수) 개발한다`는 의미를 가지고 있다.

→ 인수 테스트는 소프트웨어 인수를 목적으로 하는 테스트이다. 소프트웨어를 인수하기 전에 명세한 요구사항(인수 조건)대로 잘 작동하는지 검증이 필요하다.

❓ Mock과 Stub은 무엇인가요?

🍏 Mock

→ 스마트폰을 전시해 놓고 파는 곳에 가보면 목각폰이라고 말하는 Mock up 폰이 존재합니다. 이는 가짜 휴대폰을 이야기합니다. 실제와 동일한 기능을 하지는 않지만 대략 이렇게 생겼고, 크기는 이렇다, 어떤 기능이 대강 이렇게 동작할 것이라고 알려주는 용도입니다.

→ 테스트에서는, 호출 시 동작이 잘 되었는지를 확인하는데 사용합니다.

🍏 Stub

→ Stub 이라는 단어가 내포하는 바가, 전체 중 일부라는 뜻입니다. 모든 기능 대신 일부 기능에 집중하여 임의로 구현합니다. 일부 기능이라함은 테스트를 하고자 하는 기능을 의미합니다.

❗**Stub은 상태 검증을, Mock은 행동 검증을 사용한다는 차이점이 있습니다**. Stub에서 상태 확인을 사용하려면 확인을 돕기 위해 Stub에서 몇 가지 추가 메서드를 만들어 사용합니다. Mock 객체는 동작 검증을 사용하며 Stub은 어떤 방식으로도 사용할 수 있습니다.

❓ 둘 중 어떤 것을 사용해야 하나요?

→ 상태 검증과 행동 검증 선택을 해야합니다. 이를 위해 컨텍스트를 고려해야 합니다.
→ 가장 먼저 고려해야 할 것은 컨텍스트입니다. 여기서 이야기하는 컨텍스트는 객체가 협력해야 할 대상이 합당한 관계인지 어색한 관계인지를 따지는 것입니다.
→ 어색한 관계일 경우 고민할 필요 없이 Mock을 사용해 행동 검증을 진행하고 그렇지 않다면 상태 검증(Stub)을 사용합니다.

❓격리된 테스트는 무엇을 이야기하는건가요?

→ 데이터베이스와 같은 공유 자원을 사용하는 테스트는 실행 순서에 따라 성공, 실패 여부가 결정되는 비결정적인 테스트가 될 수 있다.
→ 이런 비결정적 테스트는 실패하면 버그가 원인인지, 비결정적 동작이 원인인지 알기 힘들다. 따라서, 테스트는 실행 순서에 상관 없이 독립적으로, 결정적으로 실행되어야한다.
→ 테스트 격리는 공유 자원을 사용하는 여러 테스트끼리 격리하여 서로 영향을 주고 받지 못하게 하는 기법이다.

⚠️ Test Code의 필요성은 변경의 여파를 최소화해주는데 도움을 준다고 생각합니다. 비지니스 정책이 변경 됐을 시, 테스트 코드를 작성했다면 어디서 예외가 나타나는지 빠르게 알 수 있고 후에 리팩토링에도 도움이 됩니다.

---

📚 Reference

[격리된 테스트 (Isolated Test) (feat. Spring 에서 테스트 격리하기)](https://hudi.blog/isolated-test/)

[[tdd] 인수테스트, 단위테스트, 통합테스트, 전 구간 테스트](https://joont92.github.io/tdd/%EC%9D%B8%EC%88%98%ED%85%8C%EC%8A%A4%ED%8A%B8-%EB%8B%A8%EC%9C%84%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%86%B5%ED%95%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%A0%84-%EA%B5%AC%EA%B0%84-%ED%85%8C%EC%8A%A4%ED%8A%B8/)

[testing - stub, mock, spy 차이는?](https://luran.me/343)

[Mock은 Stub이 아니다(Mocks Aren't Stubs)](https://jaime-note.tistory.com/330)