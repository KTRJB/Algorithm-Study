## 📌 Hash Table
- 해시 테이블(hash table), 해시 맵(hash map), 해시 표는 컴퓨팅에서 `키를 값에 매핑할 수 있는 구조`인, 연관 배열 추가에 사용되는 자료 구조이다.
- 해시 테이블은 원하는 값을 찾을 수 있는 배열로 해시 코드 라고도 하는 인덱스 를 계산하기 위해 해시 함수 를 사용한다.
- 조회하는 동안 키가 해시되고 결과 해시는 해당 값이 저장된 위치를 찾아낸다.
- 대부분의 해시 테이블 설계는 불완전한 해시 함수를 사용 하므로 해시 함수가 둘 이상의 키에 대해 동일한 인덱스를 생성하는 해시 충돌 이 발생할 수 있다.
### 📍 충돌 해결방법
#### 🔗 Collision resolution by chaining
- 충돌이 있는 경우(즉, 두 개의 다른 요소가 동일한 해시 값을 갖는 경우) 기존 주소값에서 두 요소를 linked list에 저장한다.

![](https://i.imgur.com/nuSAT1t.png)

- 조회 비용은 필요한 키에 대해 선택한 연결 목록의 항목을 스캔하는 비용
- 키 분포가 충분히 균일한 경우 조회의 평균 비용은 연결된 목록당 평균 키 수에만 의존
- 체인 해시 테이블은 테이블 항목 수(N)가 슬롯 수보다 훨씬 많은 경우에도 유효하다.
- 개별 연결의 경우 최악의 시나리오는 모든 항목이 동일한 연결 목록에 삽입되는 경우
- 조회 절차는 모든 항목을 검색해야 할 수 있으므로 최악의 경우 비용은 테이블의 항목 수(N)에 비례
#### 🔗 Open addressing
- 해시된 인덱스의 슬롯이 비어 있으면 항목 레코드가 해시된 인덱스의 슬롯에 삽입되고 그렇지 않으면 비어 있는 슬롯을 찾을 때까지 여러 프로브 시퀀스로 진행
- " open addressing"이라는 이름은 항목의 위치 또는 주소가 해시 값에 의해 결정되지 않는다는 사실을 나타낸다.
#### 🔗  open addressing에 사용되는 다양한 기술
- Linear Probing
    - 다음 주소 공간을 확인한다.
- Quadratic Probing
    - 선형 프로빙과 유사하게 동작하지만 간격이 1보다 크게 가져가는 방법
- Double hashing
    - 해시함수 h(k)를 적용한 후 충돌이 발생하면 다음 슬롯을 찾기 위해 또 다른 해시함수를 계산한다
### 📍 해쉬 함수
- Division Method
- Multiplication Method
- Universal Hashing
### 📍 시간 복잡도
- 공간복잡도
    - 평균 : Θ( n ) , 최악 : O(n)
- 탐색
    - 평균 : Θ( n ) , 최악 : O(n)
- 삽입
    - 평균 : Θ( n ) , 최악 : O(n)
- 삭제
    - 평균 : Θ( n ) , 최악 : O(n)
    
    
https://en.wikipedia.org/wiki/Hash_table
https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/
https://www.programiz.com/dsa/hash-table
