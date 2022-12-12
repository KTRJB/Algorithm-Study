### Judy
```swift
func radixSort(_ array: [Int], maxDigit: Int) -> [Int] {
    var arr = array
    let radix = 10  // 기수의 도메인 크기
    var bucket: [[Int]] = Array(repeating: [], count: radix)  // 버킷
    var digit = 1  // 자리수
    
    for _ in 1...maxDigit {  // 기수의 크기만큼 반복
        for i in 0..<array.count {
            bucket[(arr[i] / digit) % 10].append(arr[i])
        }
        
        arr = bucket.flatMap { $0 }  // 버킷에 들어간 순서로 정렬
        bucket = Array(repeating: [], count: radix)  // 버킷 초기화
        digit *= 10  // 자리수 증가
    }
    
    return arr
}
```

## 수꿍
- 구현
```swift
func radixSort(_ array: inout [Int]) -> [Int] {
    let radix = 10
    var done = false
    var digit = 1

    while !done {
        done = true

        var buckets: [[Int]] = []

        for _ in 0..<radix {
            buckets.append([])
        }

        for number in array {
            let numberToCompare = number / digit
            let index = numberToCompare % radix
            buckets[index].append(number)

            if done && numberToCompare > 0 {
                done = false
            }
        }

        var index = 0

        for currentBucketIndex in 0..<radix {
            let bucket = buckets[currentBucketIndex]
            for number in bucket {
                array[index] = number
                index += 1
            }
        }

        digit *= radix
    }

    return array
}

var array = [33, 721, 9, 11, 356, 44, 521]
print(radixSort(&array))

```
- 설명
```swift
func radixSort(_ array: inout [Int]) -> [Int] {
    // 0 ~ 9까지의 자리값
    let radix = 10
    // 정렬 완료 여부
    var done = false
    // 시작 자릿수
    var digit = 1

    // done이 true가 되면 반복문 종료
    while !done {
        // 먼저 done을 true로 설정
        done = true

        // 이중배열을 통해 각 자리수에 따른 배열을 관리
        var buckets: [[Int]] = []

        // 10개의 빈 배열 생성
        for _ in 0..<radix {
            buckets.append([])
        }

        // 정렬하고자 하는 배열의 수만큼 반복
        for number in array {
            // 비교할 자릿수에 따라 원래의 숫자를 해당 자릿수로 나누기
            let numberToCompare = number / digit
            // bucket에 담길 인덱스
            // 즉, 0~9 까지의 값 중 어디에 들어가야할 지
            // 나머지를 통해 확인 가능
            let index = numberToCompare % radix
            // 해당 자리수의 숫자값을 인덱스로 하여
            // 숫자를 각가의 bucket에 추가
            buckets[index].append(number)

            // 비교할 숫자가 0~9 사이에 들어간다면
            // 반복문 계속 진행
            // 만약 비교할 숫자가 0~9 사이에 들어가지 못한다면
            // 더이상 비교하지 않아도 됨을 의미하므로
            // done은 위에서 설정한 바처럼 true가 됨
            if numberToCompare > 0 {
                done = false
            }
        }

        // array에 접근하는 index
        var index = 0

        for currentBucketIndex in 0..<radix {
            // bucket 하나하나 접근
            let bucket = buckets[currentBucketIndex]
            // 해당 bucket에 있는 숫자를 차례대로
            // 원래의 array에 있던 숫자를 대체
            for number in bucket {
                array[index] = number
                index += 1
            }
        }

        // 다음 자릿수로 넘어가기 위한 식
        digit *= radix
    }

    return array
}

// 정렬이 잘 되는지 확인
var array = [33, 721, 9, 11, 356, 44, 521]
print(radixSort(&array))

```

### Yeton
```swift
func radixSort(_ array: [Int]) -> [Int] {
    var newArr = array
    let radix = 10
    var digit = 1
    var done = false
    
    while !done {
        var buckets: [[Int]] = []
        done = true
        
        for _ in 0..<radix {
            buckets.append([])
        }
        
        for num in newArr {
            let checkToRemove = num / digit
            buckets[checkToRemove % radix].append(num)

            if done && checkToRemove > 0 {
                done = false
            }
        }

        var i = 0
        for j in 0..<radix {
            let bucket = buckets[j] // 10,20
            for number in bucket {
                newArr[i] = number as! Int
                i += 1
            }
        }

        digit *= radix
    }

    return newArr
}

radixSort([33, 721, 9, 11, 356, 44, 521])
```

### Groot
```swift
func radixSort(_ value: [Int]) -> [Int] {
    let radix = 10 // 0...9까지 숫자를 의미
    var done = false // 언제까지 반복할 지(최대 자릿수)
    var digits = 1 // 1의 자리 
    var result = value 
    
    while !done { 
        done = true // 첫 반복부터 완료가 됬다고 해주고, 내부에 존재하는 반복문에서 값을 변경
        var buckets: [[Int]] = Array(repeating: [], count: radix) // 각 자릿수를 담을 버켓
        
        for number in result { 
            let remainingPart = number / digits // 1의 자리 , 10의 자리 ...
            let digit = remainingPart % radix // 각 자릿수의 index에 넣어주기 위해 나머지를 구한다.
            buckets[digit].append(number) // 각 자릿수에 맞게 수를 할당
            
            if remainingPart > 0 { // remainingPart이 모두 0이면 그 자릿수의 수가 없다고 판단 -> 정렬완료(반복문 종료)
              done = false
            }
        }

        digits *= radix // 다음 자릿수를 비교하기 위함
        result = buckets.flatMap { $0 } // 버켓에 있는 수를 정렬해서 결과에 넣어줌
    }
    
    return result
}
```
