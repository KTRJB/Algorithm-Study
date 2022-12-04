## 01. 거품 정렬(Bubble Sort)
### 수꿍
- 구현
```swift
var array = [5, 122, 567, 33, 1, 25]

for i in 0..<array.count {
    for j in 0..<array.count - i - 1{
        if array[j] > array[j + 1] {
            array.swapAt(j, j + 1)
        }
    }
}

for i in 0..<array.count {
    print(array[i])
}
```

- 설명
```swift
// 두 개의 for문을 통하여 시간 복잡도가 나옴
// 첫번째 for문이 없다면 결국 한번의 cycle만 돌린 것에 불과
for i in 0..<array.count {
    // 여기서 i만큼 빼주는 이유는 뒤의 값들은 cycle이 돌 때마다
    // 가장 큰 수가 배치되어 있을 것이기 때문에
    // 굳이 다시 비교를 할 필요가 없음!
    // 이렇게 해야 (n - 1) -> (n - 2) -> ... -> 2 -> 1 만큼 비교할 수 있음
    for j in 0..<array.count - i - 1{
        // 더 큰 수가 왼쪽에 위치한다면 두 수의 위치를 바꿔
        // 가장 뒤로 갈 수 있도록 swap
        if array[j] > array[j+1] {
            array.swapAt(j, j+1)
        }
    }
}

// 최종적으로 버블 정렬이 잘 되었는지 확인
for i in 0..<array.count {
    print(array[i])
}
```
### 그루트
- 구현
```swift
func bubbleSort(array: [Int]) -> [Int] {
    var temp = [Int]()
    var result = array
    
    while result != temp {
        temp = result
        
        for index in 0...result.count - 2 {
            if result[index] > result[index + 1] {
                let number = result[index]
                result[index] = result[index + 1]
                result[index + 1] = number
            }
        }
    }
    
    return result
}
```
- 설명
```swift
func bubbleSort(array: [Int]) -> [Int] {
    var temp = [Int]()
    var result = array
    
    while result != temp { // 정렬을 통해 변경이 되었는지를 체크하기 위함
        temp = result
        
        for index in 0...result.count - 2 { // 마지막 값은 다음 다음값이 없기 때문에 비교하지 않고 마지막에서 두번째 값까지만 비교함
            if result[index] > result[index + 1] { // 다음 값과의 크기를 하나씩 비교해가며 스위칭
                let number = result[index]
                result[index] = result[index + 1]
                result[index + 1] = number
            }
        }
    }
    
    return result
}
```

### Judy
```swift
func bubbleSort(_ array: [Int]) -> [Int] {
    var arr = array

    for _ in 0..<array.count {
        for j in 0..<array.count-1 {
            if arr[j] > arr[j+1] {
                let temp = arr[j+1]
                arr[j+1] = arr[j]
                arr[j] = temp
            }
        }
    }
    
    return arr
}
```
