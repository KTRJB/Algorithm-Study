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
