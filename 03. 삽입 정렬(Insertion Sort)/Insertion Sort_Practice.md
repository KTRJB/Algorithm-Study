## 03. 삽입 정렬(Insertion Sort)
### 수꿍
- 구현
```swift
var array = [9, 3, 2, 66, 754, 12, 1, 7777]

for i in 1..<array.count {
    for j in stride(from: i, to: 0, by: -1) {
        if array[j - 1] > array[j] {
            array.swapAt(j - 1, j)
        }
    }
}

for i in 0..<array.count {
    print(array[i])
}
```
- 설명
```swift
// 정렬은 두 번째 요소부터 시작하므로
// 1부터 range가 시작
for i in 1..<array.count {
    // 현재 인덱스로부터 이전 인덱스로 비교
    // 역순으로 접근하기 위해 stride 함수 사용
    // while을 이용하여 index가 0 아래로 안 가게도 작업 가능
    // stride 함수에 파라미터 to 와 through는 차이가 존재
    // to => 해당 범위 미포함
    // through => 해당 범위 포함
    for j in stride(from: i, to: 0, by: -1) {
        // 현재 인덱스 값이 이전 인덱스의 값보다 작으면 swap
        if array[j - 1] > array[j] {
            array.swapAt(j - 1, j)
        }
    }
}

for i in 0..<array.count {
    print(array[i])
}
```
