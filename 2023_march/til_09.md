
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

🍏 Request에서 get()를 호출할 때보다 Session을 통해 값을 가져오는 것이 속도 측면에서 유리합니다.

→ HTTP 요청은 클라이언트와 서버 간의 통신을 위해 매번 새로운 연결을 설정해야 합니다. 이로 인해 요청마다 새로운 연결을 맺고 헤더를 포함한 많은 양의 데이터를 전송해야 하므로, 요청의 반복적인 호출이 많은 경우에는 상당한 시간과 리소스가 소비될 수 있습니다.

→ 반면에, Session 객체를 사용하면 서버와의 연결을 한 번만 설정하고, 이후에는 해당 세션에서 데이터를 읽거나 쓰는 방식으로 통신할 수 있습니다. 이렇게 되면 요청마다 새로운 연결을 설정하지 않으므로, 통신하는 데 필요한 시간과 리소스를 줄일 수 있습니다.

→ 또한, Session은 내부적으로 커넥션 풀을 사용하여 서버와의 연결을 최적화합니다. 이렇게 되면 서버와의 연결을 캐싱하고 재사용함으로써, 요청마다 연결을 설정하고 해제하는 과정을 건너뛸 수 있으므로 더욱 빠른 속도를 기대할 수 있습니다.

→ 따라서, get() 메서드를 사용하는 것보다 Session 객체를 사용하여 데이터를 가져오는 것이 속도 측면에서 유리한 이유는 연결 설정과 해제에 소요되는 비용을 줄일 수 있으며, 내부적으로 연결을 최적화하여 빠른 데이터 전송이 가능하기 때문입니다.

🍏 multiprocess Pool에는 어떤 함수가 있고 무슨 역할을 수행하는지 알아보자

→ 파이썬 병렬 프로그래밍을 수행하던 중 제공되는 함수의 의미를 정확하게 알지 못하고 사용한 자신을 발견했다. 따라서, 사용하고 있는 함수를 살펴보는 시간을 가져보겠다.

→ multiprocessing.Pool은 파이썬의 내장 모듈인 multiprocessing의 하위 모듈 중 하나로, 병렬처리를 위한 Pool 객체를 제공합니다. 이 Pool 객체는 여러 프로세스들을 생성하여 작업을 분산 처리하며, **작업이 완료될 때까지 기다린 후 결과를 반환**합니다.

1. map(func, iterable[, chunksize]): 함수 func를 iterable의 각 항목에 대해 적용한 결과를 리스트로 반환합니다. 여러 개의 프로세스를 사용하여 작업을 병렬 처리합니다.
2. imap(func, iterable[, chunksize]): map과 비슷하나, 결과를 반환하는 순서가 보장되지 않습니다. 대신에 iterator를 반환합니다.
3. imap_unordered(func, iterable[, chunksize]): imap과 비슷하나, 결과를 반환하는 순서가 보장되지 않습니다.
4. apply(func[, args[, kwds]]): 함수 func를 인수 args와 kwds를 사용하여 호출한 결과를 반환합니다. 하나의 프로세스를 사용하여 작업을 처리합니다.
5. async_apply(func[, args[, kwds[, callback[, error_callback]]]]): apply와 비슷하나, 비동기 방식으로 작업을 처리합니다. 콜백 함수와 에러 콜백 함수를 사용할 수 있습니다.
6. close(): 더 이상 작업을 받지 않고 Pool 객체를 종료합니다. 작업이 완료될 때까지 기다립니다.
7. terminate(): 모든 작업을 즉시 중단하고 Pool 객체를 종료합니다.
8. join(): 모든 작업이 완료될 때까지 기다립니다.

➕ pool.close()와 pool.join()은 Pool 객체를 사용한 작업이 완료될 때 필요한 메서드입니다. close()는 더 이상 Pool 객체에 새로운 작업을 추가하지 않는 것을 명시적으로 선언하고, join()은 모든 작업이 완료될 때까지 대기하는 메서드입니다.

❓ 사용하고 있는 pool.async_apply는 어떤 방식으로 동작할까?

→ pool.apply_async는 multiprocessing.Pool 객체를 사용하여 비동기적으로 함수를 호출하는 메서드입니다. apply_async 메서드를 사용하면 함수 호출을 바로 반환하고, 나중에 반환값을 얻을 수 있는 AsyncResult 객체를 반환합니다.



```python

import multiprocessing

def square(x):
    return x * x

if __name__ == '__main__':
    pool = multiprocessing.Pool()
    result = pool.apply_async(square, args=(5,))
    print(result.get())  # 25
    pool.close()
    pool.join()
```

→ 위 예제에선 square 함수를 apply_async 메서드를 사용하여 호출하고, 반환된 AsyncResult 객체에서 결과를 얻어 출력합니다. 최종적으로, Pool 객체를 종료합니다.

