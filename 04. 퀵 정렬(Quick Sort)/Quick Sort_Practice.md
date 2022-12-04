## 04. 퀵 정렬(Quick Sort)
### 수꿍
- 구현
```swift
var array = [4, 1, 666, 72, 23562, 6]

func quickSort(_ array: [Int]) -> [Int] {
    guard let pivot = array.first, array.count > 1 else {
        return array
    }

    let left = array.filter { $0 < pivot }
    let right = array.filter { $0 > pivot }

    return quickSort(left) + [pivot] + quickSort(right)
}

print(quickSort(array))
```
- 설명
```swift
func quickSort(_ array: [Int]) -> [Int] {
    // 크기 비교를 위해 기준이 되는 요소(pivot)를 배열의 첫 요소로 선택
    // 배열의 크기가 0이거나 1일 경우, 정렬 과정이 필요없기 때문에 조건에 추가
    guard let pivot = array.first, array.count > 1 else {
        return array
    }

    // pivot을 기준으로 필터링하여
    // 크기가 작은 배열을 왼쪽에,
    // 크기가 큰 배열을 오른쪽에 배치
    let left = array.filter { $0 < pivot }
    let right = array.filter { $0 > pivot }

    // 그리고 배열의 크기가 0이나 1이 될때까지 순환 함수로 돌림
    // 그리고 나서 결합을 실시
    return quickSort(left) + [pivot] + quickSort(right)
}

// 최종적으로 잘 정렬되었는지 확인
print(quickSort(array))
```
### 그루트
- 구현
```swift
func quickSort(array: [Int]) -> [Int] {
    guard let first = array.first else { return array }
    
    let pivot = first
    var left = [Int]()
    var right = [Int]()
    
    array.enumerated().filter { $0.offset != 0 }
        .forEach {
            if $0.element > pivot {
            right.append($0.element)
        } else if $0.element <= pivot {
            left.append($0.element)
        }
    }
    
    return quickSort(array: left) + [pivot] + quickSort(array: right)
}
```
- 설명
```swift
func quickSort(array: [Int]) -> [Int] {
    guard let first = array.first else { return array } // 빈 배열을 확인
    
    let pivot = first // pivot을 처음 값으로 설정
    var left = [Int]()
    var right = [Int]()
    
    array.enumerated().filter { $0.offset != 0 } // filter를 통해 pivot을 제거해주고 pivot 보다 작으면 left에 추가 크면 right에 추가하는 방식
        .forEach {
            if $0.element > pivot {
            right.append($0.element)
        } else if $0.element <= pivot {
            left.append($0.element)
        }
    }
    
    return quickSort(array: left) + [pivot] + quickSort(array: right) // 양쪽 left와 right의 index가 0이 될때까지 계속 반복하다 마지막으로 pivot  넣고 합친다.
}
```
