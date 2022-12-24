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
