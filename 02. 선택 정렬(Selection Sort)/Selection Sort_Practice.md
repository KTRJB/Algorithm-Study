## 02. 선택 정렬(Selection Sort)
### 수꿍
- 구현
```swift
var array = [50, 25, 5, 3, 66, 3939, 11]

for i in 0..<array.count - 1 {
    var minNumber: Int = array[i]
    var location: Int = i

    for j in i + 1..<array.count {
        if minNumber > array[j] {
            minNumber = array[j]
            location = j
        }
    }

    if i != location {
        array.swapAt(i, location)
    }
}

for i in 0..<array.count {
    print(array[i])
}
```
- 설명
```swift
// 스캔 작업을 (배열 요소의 갯수 - 1) 만큼 반복하면 전체 배열이 정렬
// count에서 - 1을 하는 이유는, 만약 5개 요소중 4개를 작은 값부터 정렬하면
// 나머지 1개는 가장 큰 값으로, 자동으로 마지막 index에 위치
for i in 0..<array.count - 1 {
    // 가장 작은 숫자를 임의로 해당 인덱스의 숫자로 설정
    // 어차피 더 작은 숫자를 만나면 대체할 것이니 걱정 X
    var minNumber: Int = array[i]
    // 현재 가장 작은 숫자의 인덱스 저장
    var location: Int = i

    // 최소값을 찾는 스캔 작업
    // 현재 지정된 인덱스의 숫자와 나머지 숫자들을 비교하기 위하여
    // i + 1 부터 인덱스가 시작
    for j in i + 1..<array.count {
        // 더 작은 최소값을 발견할 시의 조건문
        if minNumber > array[j] {
            // 최소값 대체
            minNumber = array[j]
            // 최소값을 가지고 있는 인덱스로 대체
            location = j
        }
    }

    // 현재 인덱스에 있는 숫자가 최소값이면 위치 변견 필요 X
    // 그렇지 않다면 swap 작업 필요
    if i != location {
        array.swapAt(i, location)
    }
}

// 최종적으로 정렬이 잘 되었는지 확인
for i in 0..<array.count {
    print(array[i])
}

```

### 그루트
- 구현
```swift
func selectionSort(array: [Int]) -> [Int] {
    var count = 0
    var result = array
    
    while count != result.count {
        let minIndex = count
        
        for index in count...result.count - 1 {
            if result[minIndex] > result[index] {
                let temp = result[minIndex]
                result[minIndex] = result[index]
                result[index] = temp
            }
        }
        
        count += 1
    }
    
    return result
}
```
- 설명
```swift
func selectionSort(array: [Int]) -> [Int] {
    var count = 0 // 처음 값을 선택해서 시작함.
    var result = array
    
    while count != result.count { // 선택된 값이 마지막 값이면 정렬이 끝났다고 생각, 빠져나감
        let minIndex = count
        
        for index in count...result.count - 1 {
            if result[minIndex] > result[index] { // 선택된 값보다 작은값이 존재하면 스위칭 
                let temp = result[minIndex]
                result[minIndex] = result[index]
                result[index] = temp
            }
        }
        
        count += 1
    }
    
    return result
}
```
