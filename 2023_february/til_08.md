
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

❓ HttpServletRequest와 HttpSession의 차이점

→ 둘의 차이점을 알아보기 이전 프로젝트에서 사용하는 이유를 적어보자면 Http의 특성인 stateless 시 발생하는 문제점을 해결하기 위함입니다.

→ HttpStatless 특징은 웹의 확장 측면에선 장점을 갖지만 상태를 저장하지 않기 때문에 상태를 저장할 수 있는 다른 방법을 사용해야 합니다.

→ 다른 방법으로 Session을 사용하고자 할 때, HttpServletRequest와 HttpSession의 도움을 받아 Session을 발급받을 수 있습니다.

→ HttpServletRequest와 HttpSession의 차이점은 메모리에서 살아있는 기간이 다릅니다. HttpSession은 Client가 접속 중인 동안에만 존재하지만 HttpServletRequest는 Request 중인 동안에만 존재합니다.

❓ Session 발급의 위치는 Controller Layer? Service Layer?

→ Service Layer에 두는 것이 좋다고 생각됩니다. Controller는 "요청"을 처리하는 Layer이며 애플리케이션이 구동되는 위치는 Service Layer의 책임이기 때문입니다.

→ 따라서, 구현 시 Mapping Controller에 HttpServletRequest를 받아오는 것이 아닌 HttpSession을 사용했습니다.

🍏 Interceptor의 경우 스프링에서 관리되지 때문에 스프링 내의 모든 객체에 접근이 가능합니다. 즉, 빈을 관리하는 스프링 컨텍스트 내에 있어서 생성된 빈들에 자유롭게 접근할 수 있습니다.

→ Interceptor를 통해 얻을 수 있는 장점은
1. 공통 코드 사용으로 코드 재사용성 증가
2. 메모리 낭비, 서버 부하 감소
3. 코드 누락에 대한 위험성 감소