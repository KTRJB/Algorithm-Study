## 수꿍
- 구현
```swift
func countingSort(array: [Int]) -> [Int] {
    let maxElement = array.max() ?? 0

    var countArray = [Int](repeating: 0, count: Int(maxElement + 1))

    for element in array {
        countArray[element] += 1
    }

    for index in 1...array.count {
        let sum = countArray[index] + countArray[index - 1]
        countArray[index] = sum
    }

    var sortedArray = [Int](repeating: 0, count: array.count)

    for index in stride(from: array.count - 1, through: 0, by: -1) {
        let element = array[index]
        countArray[element] -= 1
        sortedArray[countArray[element]] = element
    }

    return sortedArray
}

let myArray = [1, 5, 4, 4, 3, 7, 3]

print(countingSort(array: myArray))
```
- 설명
```swift
func countingSort(array: [Int]) -> [Int] {
    // countArray의 배열 크기는 배열내 정수의 최대값만큼!
    let maxElement = array.max() ?? 0

    // 0부터 배열의 최대값에 이르기까지의 countArray 생성
    var countArray = [Int](repeating: 0, count: Int(maxElement + 1))

    // 사용자가 입력한 array에 해당 숫자가 몇개 존재하는지 counting
    for element in array {
        countArray[element] += 1
    }

    // countingSort의 전제가 양의 전수이므로 0은 당연히 0일 것임
    // 따라서 범위가 양의 정수의 최소값인 1부터 시작
    for index in 1...array.count {
        // 누적합 계산
        let sum = countArray[index] + countArray[index - 1]
        countArray[index] = sum
    }

    // 반환하고자할 배열을 생성
    // 이렇게 생성해도 되고 그냥 입력받은 배열을 복사해도 될 것 같음
    var sortedArray = [Int](repeating: 0, count: array.count)

    // 배열의 수에서 1을 뺀 값인 최대 인덱스이기 때문에 array.count - 1
    // 0번 인덱스까지, -1의 보폭으로 반복
    for index in stride(from: array.count - 1, through: 0, by: -1) {
        // 입력받은 배열의 뒤부터 원소를 추출
        let element = array[index]
        // countArray내에서 해당 원소의 값이 있는 위치로 가서
        // count를 하나 줄여줌
        countArray[element] -= 1
        // count를 하나 줄여줌으로써 본래의 위치에 정착 가능
        // 즉, 이번 배열의 경우 마지막 원소가 3인데
        // countArray에서는 0부터 값이 시작해 인덱스가 3이지만
        // sortedArray에서는 인덱스 2에 들어가야 하므로
        // -1이 들어간 것임
        sortedArray[countArray[element]] = element
    }

    return sortedArray
}

// 사용자 정의 배열
let myArray = [1, 5, 4, 4, 3, 7, 3]

// 정렬이 제대로 되는지 확인
print(countingSort(array: myArray))
```

## 예톤

```swift
func 계수정렬(num: [Int]) -> [Int] {
    var arr = Array(repeating: 0, count: num.max()!)
    var result: [Int] = []
    num.forEach {
        arr[$0 - 1] += 1
    }
    
    for (index, num) in arr.enumerated() {
        for _ in 0..<num {
            result.append(index + 1)
        }
    }
    return result
}
```

## 그루트

```swift
func countingSort(_ array: [Int]) -> [Int] {
    var tempArray = Array(repeating: 0, count: (array.max() ?? 0) + 1) // 가장 큰 값의 크기를 가진 배열을 할당
    var result = [Int]()
    
    for number in array {
        tempArray[number] += 1 // 각 값들의 개수를 배열에 저장
    }
    
    for index in 0..<tempArray.count {
        if tempArray[index] != 0 { // 0이 아닌 값들만 처리하기 위함. -> 존재하는 수만 for문을 돌림
            for _ in 0..<tempArray[index] { 
                result.append(index) // index 값의 개수만큼 새로운 배열에 
            }
        }
    }
    
    return result
}
```

## Judy
```swift
func countingSort(_ array: [Int], with max: Int) -> [Int] {
    var countingArray = Array(repeating: 0, count: max + 1)	// 계수 배열
    var sortedArray = Array(repeating: 0, count: array.count)	// 정렬된 값을 넣을 배열
    
    for element in array {
        countingArray[element] += 1	 // 해당 숫자인 인덱스의 값을 +1
    }
    
    for i in 1..<countingArray.count {
        countingArray[i] += countingArray[i-1]	// 누적합 배열로 만들기
    }
    
    for j in stride(from: array.count - 1, through: 0, by: -1) { 
        let sortingValue = array[j]	// 정렬할 값 = 인덱스가 될 값
        sortedArray[countingArray[sortingValue] - 1] = sortingValue	// 정렬한 배열[누적합 배열[정렬할 값] -1]
        countingArray[sortingValue] -= 1 // 정렬했으니 해당 부분의 누적합을 -1
    }
    
    return sortedArray
}
```
