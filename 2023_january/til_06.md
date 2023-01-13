
---

🍎 프로젝트 관련
→ 주소 값을 기반으로 외부 API와 통신해 좌표를 얻어 올 수 있었습니다. 여기서 고민을 해봐야 할 부분이 생겼습니다. 바로 외부API 요청에 대한 응답 시 제 계정에 부여된 ClientId, ClientKey를 어떤 방식으로 관리하는가 입니다.
→ 노출을 관리해야하는 이유는 외부에 ClientId, ClientKey가 노출되면 불특정 사용자가 API를 사용하게 될 것이고 이는 많은 문제를 유발할 수 있기 때문입니다.

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

❓ 외부에 노출되면 안되는 데이터는 어떤 방식으로 관리해야 안전할까요?
→ 찾아본 결과 크게 세 가지 방법이 존재한다.

  * Hard Coding : 필드에 노출되는 값을 정의하고 사용한다.
  * 환경 변수에 등록해 사용 : \@Value를 통해 값을 가져와 사용
  * Tool의 도움을 받아 사용

  🍏 Hard Codeing 시 장/단점
    → 세 가지 방법 중 가장 구현하기 쉬우며 .gitignore 시 해당 Key를 명시한 클래시 파일을 제거해줘야 한다.

  🍏 환경 변수에 등록해 사용 시 장/단점
    → Hard Coding 방법보단 좋지만 외부의 노출을 막기 위해 .gitignore를 설정해야하고 배포 시 application.yml에 직접 넣어주어야 한다.
    → 배포 시 존재하지 않는 application.*. 즉, 필요한 설정 파일을 직접 넣어야 한다.

  🍏 외부에서 제공하는 Tool에 도움을 받아 사용하는 경우
    → 위 두개의 과정보다는 복잡하지만 좋은 보안을 유지할 수 있다.
    → 외부 서비스 연동을 제공하는 Spring Cloud Config or Aws System Manager, AppConfig 등을 사용해 처리할 수 있지만 별도의 관리가 필요하며 서비스 사용 비용이 발생할 수 있다.
    → 환경 변수를 외부에서 주입하는 방법도 존재한다. Github Secrete를 사용하면 외부에서 주입해 사용할 수 있다.

  ❓ 그래서 어떤 방법을 택하셨나요?
    → Hard Coding으로 작성 후 향후 CI/CD를 도입할 때 Github Action에서 제공하는 Secrete 기능을 사용해 값을 처리할 계획입니다.

❓ String type의 URL 데이터를 URL encoder를 사용해 변경하는 이유는 무엇일까요?
→ URL에는 여러가지 규칙이 있고 그 규칙에 사용되는 문자들이 정해져 있기 때문에 특정한 값을은 규칙에 맞게 변환되어야 합니다.
→ 또는 쿠키와 같이 한글을 표현하지 못하는 경우 한글을 ASCII 값으로 인코딩해줘야 합니다.

💻 ChatGPT는 아래와 같이 답을 줬습니다.
→ UTF-8 is a widely-used and well-supported character encoding, it is less likely to cause compatibility issues than other encodings. This can be especially important when working with data from different sources and systems.

❓ 비동기란 무엇인가요?
→ 일을 시작 시키고, 작업이 끝날때까지 **안 기다린다.**
  → Main Thread가 다른 Thread에게 일을 하도록 시킨 후 안 기다리고 다른 일 처리를 시작할 수 있다.
  → 예를 들어 웹에서 처리 시간이 오래 걸리는 일을 처리해야 할 때 Main Thread가 직접 처리를 한다면 후에 쌓인 일들이 밀려있을 것이다. 이는 사용자에게 늦은 랜더링을 제공할 수도 있다. 해당 프로세스에서 운영되고 있는 Thread 가 여러개라면 Main Thread가 다른 Thread에 일을 넘기고 다음 일을 처리하는 것이 더 효율적이다
  ❓ 비동기가 일반적으로 필요한 이유는 무엇인가요?
  → 대부분 서버와의 통신(Network 작업) 때문입니다.

❓ 동기란 무엇인가요?
→ 작업을 시작 시키고, 뿐만아니라 작업이 끝날때까지 **기다린다.**
  → Main Thread가 다른 Thread에게 일을 하도록 시킨 후 그 작업이 끝나길 기다렸다가 다음 일을 진행한다.

❓ 직렬 처리와 동시 처리의 차이점은 무엇인가요?
→ 직렬 처리는 일들을 하나의 Thread에서 담당해서 처리하는 것을 말합니다. 다른 한개의 Thread에서.
→ 동시 처리는 몇개의 Thread로 분산해 작업을 처리하는 것을 말합니다. 몇개의 Thread로 분산할지는 시스템이 알아서 결정합니다. 중요한 것은 여러개의 다른 Thread로 분산 처리한다는 것입니다.
  ❓ 분산 처리 하려는 것이라면, 무조건 **동시 처리** 가 좋아보이는데 왜 **직렬 처리**가 필요할까요?
  → 작업의 순서가 필요할 땐 직렬 처리가 필요하기 때문입니다. 동시 처리는 각자 독립적이지만 유사한 여러개의 작업을 처리할 때 사용됩니다.

❗ 따라서, 동시성 프로그래밍을 이야기할 때 성능/반응성을 이야기하고 나아가 최적화가 이야기되는 것입니다.
---

📚 Reference
[동기(sync) 비동기(async)의 개념에 대한 가장 직관적인 이해](https://www.inflearn.com/course/sync-async-개념-이해/dashboard)
