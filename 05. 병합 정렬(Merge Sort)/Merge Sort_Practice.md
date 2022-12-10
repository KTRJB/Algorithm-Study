## 05. 병합 정렬(Merge Sort)
### 수꿍
- 구현
```swift
func mergeSort(list: [Int]) -> [Int] {
    if list.count <= 1 {
        return list
    }

    var leftList: [Int] = []
    var rightList: [Int] = []

    let mid = list.count / 2 
    leftList += list[0..<mid]
    rightList += list[mid..<list.count]

    var left = mergeSort(list: leftList)
    var right = mergeSort(list: rightList)

    return merge(left, right)
}

private func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var result: [Int] = []
    var leftArray = left
    var rightArray = right

    while !leftArray.isEmpty && !rightArray.isEmpty {
        let value = leftArray[0] < rightArray[0] ? leftArray.remove(at: 0) : rightArray.remove(at: 0)
        result += [value]
    }

    if !leftArray.isEmpty {
        result += leftArray
    }

    if !rightArray.isEmpty {
        result += rightArray
    }

    return result
}


let list = [76, 33, 21, 444, 2, 595, 99]
print(mergeSort(list: list))

```
- 설명
```swift
func mergeSort(list: [Int]) -> [Int] {
    // 병합정렬을 통해 작은 단위로 분리하였을때
    // 리스트의 원소가 하나밖에 남지 않으면 그대로 반환
    if list.count <= 1 {
        return list
    }

    // 퀵 정렬과 유사하게 좌측 리스트와 우측 리스트로 배열
    var leftList: [Int] = []
    var rightList: [Int] = []

    // 좌우 리스트의 원소의 갯수를 반으로 나눔
    // 홀수인 경우에도 mid를 Int로 설정되기 때문에
    // 소수점을 버리고 정수값으로 치환
    // 따라서 리스트의 index에 소수값이 아닌 정수값이 들어가
    // 에러가 발생하지 않음
    let mid = list.count / 2
    leftList += list[0..<mid]
    rightList += list[mid..<list.count]

    // 리스트가 최소한의 단위가 될때까지 재귀
    var left = mergeSort(list: leftList)
    var right = mergeSort(list: rightList)

    // 비교 및 병합 함수 적용
    return merge(left, right)
}

// mergeSort 구현을 위한 내부 함수라 private 처리를 해 봄
private func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    // 최종적으로 return할 배열 생성
    var result: [Int] = []

    // left, right는 let이기 때문에
    // 자유롭게 담을 배열 생성
    var leftArray = left
    var rightArray = right

    // 좌측, 우측 배열이 모두 비어있지 않을 경우 반복
    while !leftArray.isEmpty && !rightArray.isEmpty {
        // 각 배열의 첫번째 원소를 비교하여
        // 더 작은수를 원래의 배열에서 제거하고
        // 결과 배열에 append
        let value = leftArray[0] < rightArray[0] ? leftArray.remove(at: 0) : rightArray.remove(at: 0)
        result += [value]
    }

    // 여기까지 코드가 내려온 경우라면
    // 적어도 하나의 배열이 empty인 상황
    // 따라서 나머지 한 배열에 남은 수가
    // 가장 큰 수일 것이므로 마지막 결과 배열에 추가
    if !leftArray.isEmpty {
        result += leftArray
    }

    if !rightArray.isEmpty {
        result += rightArray
    }

    return result
}


// 정렬이 잘 되는지 확인
let list = [76, 33, 21, 444, 2, 595, 99]
print(mergeSort(list: list))

```
