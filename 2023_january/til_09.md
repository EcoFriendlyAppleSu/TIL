
---

🍎 프로젝트 관련
→ Java Network을 사용해 외부 API와 통신하던 것을 Spring WebClient를 적용했습니다.
→ Spring에서 기본적으로 제공하는 RestTemplate를 사용하지 않고 WebClient 의존성을 추가해 사용한 이유는
Non-Bloacking 방식으로 요청자과 제공자 사이의 통신을 하기 위함입니다.
→ 많은 트래픽이 발생했을 때 RestTemplate보다 WebClient를 사용하는게 더 효율적이기 때문에 사용합니다.
→ h2 DB를 걷어내고 MySQL 도입했습니다.

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 Blocking과 Non-Blocking은 무엇이며 어떤 차이점이 존재하나요?
→ Blocking과 Non-Blocking을 이해하기 위해선 **제어권**을 알아야 합니다.
→ Blocking과 Non-Blocking은 A 함수가 B 함수를 호출했을 때, 제어권을 어떻게 처리하느냐에 따라 달라집니다.

  * Blocking
  → A 함수가 B 함수를 호출하면, 제어권을 A가 호출한 B 함수에 넘겨줍니다.
  → 예를 들어, MySQL에서 Connection Pool을 사용할 때 Blocking I/O를 사용합니다.

  * Non-Blocking
  → A 함수가 B 함수를 호출해도 제어권은 그대로 자신이 갖고 있습니다.
  → A 함수는 계속 제어권을 가지고 있기 때문에 B 함수를 호출한 이후에도 자신의 코드를 계속 실행한다.

---
📚 Reference
[Blocking, Non-Bloacking](https://velog.io/@nittre/%EB%B8%94%EB%A1%9C%ED%82%B9-Vs.-%EB%85%BC%EB%B8%94%EB%A1%9C%ED%82%B9-%EB%8F%99%EA%B8%B0-Vs.-%EB%B9%84%EB%8F%99%EA%B8%B0)
[Spring WebClient](https://happycloud-lee.tistory.com/220)
