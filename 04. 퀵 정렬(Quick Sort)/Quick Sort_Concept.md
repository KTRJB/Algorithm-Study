# Quick Sort
**교환 정렬**
> pivot을 기준으로 정렬한 후 다시 왼쪽, 오른쪽을 퀵 정렬 후 병합

- **분할 정복 알고리즘** - 문제를 작은 문제로 분리한 후 모아서 문제를 해결

### 특징
- pivot은 중간 크기의 값이 좋음

#### 장점
- 속도가 빠르다
- 추가 메모리 공간을 필요로 하지 않는다.

#### 단점
- 이미 정렬이 된 경우 오히려 수행시간이 더 걸린다
<br>

### 시간 복잡도
- 최선: O(nlogn)
- 평균: O(nlogn)
- 최대: O(n^2) 
<br>

### 방법
- 임의의 값을 pivot으로 선택
- 왼쪽(left)과 오른쪽(right)부터 pivot과 값을 비교
- 왼쪽 값이 pivot 보다 크고, 오른쪽 값이 pivot 보다 작으면 교환
- left와 right가 서로 만나면 해당 위치에 pivot을 삽입
- pivot을 기준으로 왼쪽, 오른쪽을 다시 quick 정렬 실행

![](https://velog.velcdn.com/images/juyoung999/post/46a6ec03-2949-47ed-93df-e1952268f6de/image.png)
<br>

---
**참고 링크**<br>
[위키피디아 - 퀵 정렬](https://ko.wikipedia.org/wiki/%ED%80%B5_%EC%A0%95%EB%A0%AC)<br>
[퀵 정렬](https://gmlwjd9405.github.io/2018/05/10/algorithm-quick-sort.html)
