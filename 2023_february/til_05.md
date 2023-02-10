
---
🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 Mybatis의 xml 파일에서는 부등호를 **TAG**로 인식하기 때문에 "The content of elements must consist of well-formed character data or markup" 예외가 발생합니다.
→ 이를 해결하기 위해선 **<![CDATA[Content]]>로 감싸 사용합니다.

❓ 사전을 정렬하기 위해서 필요한 자료구조 trie는 무엇인가요?
→ 자료구조 trie는 특별히 문자열에서 검색을 빠르게 해주는 자료구조입니다.
→ 문자열을 이진 탐색으로만 찾는다면 O(logN)이 아닌 문자열 내부까지 순회를 돌아야 함으로 O(MlogN)의 시간이 소요됩니다. 이 문제를 해결하기 위해 trie라는 Tree를 사용하게 됩니다.
- Trie는 다음과 같이 구성됩니다.
1. Trie 노드는 Root Node를 비웁니다.
2. Root Node 다음 노드부터 문자열 안에 존재하는 하나의 문자를 갖는 노드로 연결합니다.
3. 각 부모노드는 자식 노드를 a부터 z까지(대문자도 마찬가지)를 가질 수 있습니다.

❓ 그렇다면 Trie 자료구조의 문제점은 없는 것일까요?
→ 문자열이 저장되는 것이 아닌 매 문자를 잘라 사용하게되어 메모리 사용량이 증가합니다.
→ Hash Table과 Binary Tree보다 데이터 삽입이 느립니다.
→ 데이터 압축, GC, 효율적인 저장을 구현하는데 어렵습니다.

❓ 사전을 정렬하기 위해 Trie 자료구조가 최고의 선택인가요?
→ 아닙니다. Trie 자료구조 이외에도 Hash table, radix tree 등 다양한 자료구조를 사용하는 것이 좋은 효율을 낼 수도 있습니다.
→ 예를 들어, 저장할 문자열의 수, 저장할 문자열의 길이, 자주 사용하는 문자열을 빈도 등을 활용하면 비단 Trie 자료구조를 사용하지 않아도 효율적으로 사전 작업을 처리할 수 있습니다.