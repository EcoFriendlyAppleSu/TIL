
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 Web Crawling 시, 사용하는 BeautifulSoup는 Scraping을 하기 위해 사용하는 패키지이고 lxml은 구문을 분석하기 위한 parser입니다.

→ response.text로 가져온 String을 lxml이라는 모듈의 해석에 의하여 의미있는 HTML 문서로 변환시켜숩니다. 이렇게 변환된 HTML 문서는 BeautifulSoup에 의해 원하는 부분을 탐색할 수 있게 됩니다.

🍏 특정 파일 실행은 Linux에서 제공하는 Scheduling입니다. Linux 계열에서 특정 시간에 특정 작업을 하는 데몬을 Cron이라고하고 Cron이 언제 무엇을 하는지 특정 파일에 저장하는 것을 Crontab이라고 합니다.

→ Cron이라는 데몬이 원하는 시간에 원하는 명령 또는 프로그램을 수행하도록 명령 리스트를 만드는 것이 **Crontab** 작업이라고 할 수 있습니다.

→ 특정 시간에 특정 작업을 해야할 때, 반복된 시간에 반복된 작업을 해야할 때, 예약 작업을 사용해야 할 때 사용합니다.

🍏 크롤링 시, main url/robots.txt를 사용하면 해당 페이지에서 Crawling 가능 여부를 알 수 있다. Disallow라고 명시되어 있는 Dir or File에 대해서는 Crawling을 할 수 없다.

❓ Crawling Scheduling 관련되어 Linux에서 제공하는 cron, crontab 기능을 사용하는 것이 옳은 방법일까?

→ 같이 프로젝트를 진행하는 팀원의 OS는 Window이며 crontab을 동일하게 설정해 프로젝트를 구성하게 된다면 Crawling된 데이터가 저장 시 두 협업자 사이에 데이터 일관성에 문제가 발생할 수 있다. 따라서, 다른 방법을 찾아야 한다.

→ github Action에서 제공하는 Scheduling을 사용하게 되면 OS의 의존성을 벗어나 협업하는 팀원과 데이터 불일치 없이 수행할 수 있는 것을 알았습니다.

❓ requirements.txt 파일은 무엇인가요?

→ 설칭된 모든 Python pkg(module)들의 목록을 저장한 파일입니다. github action configuration file 등록 시 필요한 정보를 담고 있습니다.