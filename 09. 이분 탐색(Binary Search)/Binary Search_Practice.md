## 수꿍
- 구현
```swift
func binarySearch(array: [Int], number: Int) -> Bool {
    var start = 0
    var end = array.count - 1

    while start <= end {
        let mid = (start + end) / 2
        let guess = array[mid]

        if guess == number {
            return true
        } else if guess < number {
            start = mid + 1
        } else {
            end = mid - 1
        }
    }

    return false
}

let array = [1, 4, 5, 8, 55, 293, 455]

print(binarySearch(array: array, number: 8))
```
- 설명
```swift
func binarySearch(array: [Int], number: Int) -> Bool {
    // 시작 인덱스 값은 0
    var start = 0
    // 종료 인덱스 값은 배열의 갯수 - 1
    var end = array.count - 1

    // start와 end 사이를 벗어나면
    // 해당 값 사이에 찾고자 하는 수가 존재하지 않음을 의미
    while start <= end {
        // 중간 인덱스값은 start와 end의 1/2
        let mid = (start + end) / 2
        // 배열의 중간값 추출
        let guess = array[mid]

        // 중간값과 찾고자 하는 수 비교
        if guess == number {
            // 중간값과 찾고자 하는 수가 같으면 종료
            return true
        } else if guess < number {
            // 중간값이 찾고자 하는 수보다 작으면
            // 중간값보다 작은 수는 볼 필요가 없음
            // 따라서 시작 인덱스를 중간값 이후로 재설정
            start = mid + 1
        } else {
            end = mid - 1
        }
    }

    return false
}

// 사용자 정의 배열
let array = [1, 4, 5, 8, 55, 293, 455]

// 이진 탐색이 잘 이루어지는지 확인
print(binarySearch(array: array, number: 8))
```

## 예톤


```swift
func 이분탐색(arr: [Int], num: Int) -> Bool {
    var start = 0
    var end = arr.count
    
    while start <= end {
        var mid = (start + end) / 2
        
        if arr[mid] == num {
            return true
        } else if arr[mid] < num {
            start = mid + 1
        } else if arr[mid] > num {
            end = mid - 1
        }
    }
    
    return false
}
```

## 그루트
```swift
func binarySearch(_ array: [Int], number: Int) -> Bool { 
    let sortedArray = countingSort(array) // 먼저 배열을 정렬한다.
    var left = 0 // 가장 작은 값으로 시작
    var right = sortedArray.count - 1 // 가장 큰 값으로 시작
    
    while left <= right {  // 가장 작은 값과 큰 값이 같아지면 모두 확인했다고 판단한다.
        let mid = (left + right) / 2 // 가장 작은 값과 큰 값의 중간값을 비교
        
        if number == sortedArray[mid] { // 중간 값이 찾는 값이면 true를 리턴하고 끝남.
            return true
        } else if number > sortedArray[mid] { // 찾는 값이 중간값보다 크면 시작점을 중간값 + 1 로 수정 -> 찾는 폭을 줄이기 위함
            left = mid + 1
        } else if number < sortedArray[mid] { // 찾는 값이 중간값보다 작으면 끝점을 중간값 - 1 로 수정 
            right = mid - 1
        }
    }
    
    return false
}
```
