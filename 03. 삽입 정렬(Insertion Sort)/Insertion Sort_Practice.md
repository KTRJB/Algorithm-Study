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
### 그루트
- 구현
```swift
func insertionSort(array: [Int]) -> [Int] {
    var result = array
    
    if result.count > 1 {
        for insertionIndex in 1...result.count-1 {
            for index in stride(from: insertionIndex, to: 0, by: -1) {
                if result[index] < result[index - 1] {
                    result.swapAt(index, index - 1)
                } else {
                    break
                }
            }
        }
    }
    
    return result
}
```
- 설명
```swift
func insertionSort(array: [Int]) -> [Int] {
    var result = array
    
    if result.count > 1 { // 비어있는 배열을 넣으면 실행하지 않도록 하기위함.
        for insertionIndex in 1...result.count-1 { 두번째부터 시작하고 그 앞의 값과 비교하기 위함.
            for index in stride(from: insertionIndex, to: 0, by: -1) { // stride 함수를 통해서 insertionIndex 부터 시작해서 by(-1)만큼 줄여가고 to(0)전 까지 실행하는 반복문을 구현.
                if result[index] < result[index - 1] { 
                    result.swapAt(index, index - 1)
                } else {
                    break
                }
            }
        }
    }
    
    return result
}
```

### Judy
```swift
func insertionSort(_ array: [Int]) -> [Int] {
    var arr = array
    
    for i in 1..<array.count {
        for j in 0...i {
            if arr[i] <= arr[j] {
                let temp = arr[i]
                arr.remove(at: i)
                arr.insert(temp, at: j)
                break
            }
        }
    }
    
    return arr
}
```
