# Insert Sort
**삽입 정렬**
> 이미 정렬된 부분과 비교하여 자신의 위치를 찾아 삽입

### <br>특징
#### 장점
- 안전한 정렬
- 대부분의 요소가 이미 정렬된 경우 효율적

#### 단점
- 요소 수가 적을 경우 복잡한 알고리즘 보다 유리하지만 크기가 큰 경우 적합하지 않다
<br>

### 시간 복잡도
- 최선: O(n) - 이미 정렬된 경우 
- 평균: O(n^2)
- 최대: O(n^2) - 역순으로 정렬된 경우

<br>

### 방법
- 1번째를 0번째와 비교 후 올바른 위치에 삽입
- 2번째를 0~1과 비교 후 올바른 위치에 삽입
...
- `n`번째를 0~`n-1`과 비교 후 올바른 위치에 삽입

![](https://velog.velcdn.com/images/juyoung999/post/27b99ce6-01ca-4464-a464-3037bddd0169/image.png)
<br>

[위키피디아 - 삽입 정렬](https://ko.wikipedia.org/wiki/%EC%82%BD%EC%9E%85_%EC%A0%95%EB%A0%AC)
[삽입 정렬](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html)
