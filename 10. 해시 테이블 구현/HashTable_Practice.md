## 수꿍
- 구현
```swift
var hashTable = [String?](repeating: nil, count: 3)

func hash(key: Int) -> Int {
    print(key)
    print(key % 3)
    return key % 3
}

func updateValue(_ value: String, forKey key: String) {
    guard let key = UnicodeScalar(key)?.value else {
        return
    }

    let hashAddress = hash(key: Int(key))
    hashTable[hashAddress] = value
}

func getValue(forKey key: String) -> String? {
    guard let key = UnicodeScalar(key)?.value else {
        return nil
    }

    let hashAddress = hash(key: Int(key))
    return hashTable[hashAddress]
}

updateValue("루트", forKey: "그")
updateValue("톤", forKey: "예")
updateValue("디", forKey: "쥬")

getValue(forKey: "그")
getValue(forKey: "예")
getValue(forKey: "쥬")

```
- 설명
```swift
// hashTable 배열을 생성
// swift에서는 Dictionary가 해시 테이블로 구현
// 따라서, hashTable 또한 key, value 값을 가지고 있고
// Dictionary의 key가 Hashable해야함은 해시테이블이기 때문
var hashTable = [String?](repeating: nil, count: 3)

// hash 함수
// 해시 테이블 주소값으로 변환하기 위하여
// 해시 함수를 사용하는데 이를 구현하기 위한
// 다양한 알고리즘이 존재하나
// hashTable에 대한 간단한 이해가 목적이므로
// 아래의 블로그를 참고하여 간단 구현
// https://babbab2.tistory.com/89
func hash(key: Int) -> Int {
    print(key)
    print(key % 3)
    return key % 3
}

// key, value 값을 업데이트하기 위한 함수
// key 값이 존재하면 update
// key 값이 존재하지 않는다면 create
func updateValue(_ value: String, forKey key: String) {
    // UnicodeScalar는 유니코드 스칼라 값을 반환하기 위한 함수
    // 뒤의 .value는 numeric value로 반환하기 위함
    guard let key = UnicodeScalar(key)?.value else {
        return
    }

    // key 값은 현재 UInt32 값이므로
    // Int함수를 통해 정수형으로 변환 후
    // 해시함수를 적용하여 해시 주소값을 생성
    let hashAddress = hash(key: Int(key))
    // 해시테이블의 인덱스로
    // 해시 주소값을 사용하여 value를 생성 혹은 업데이트
    hashTable[hashAddress] = value
}

// key 값을 통하여 value를 도출하는 함수
func getValue(forKey key: String) -> String? {
    guard let key = UnicodeScalar(key)?.value else {
        return nil
    }

    let hashAddress = hash(key: Int(key))
    // 해시 주소값을 사용하여 value 탐색 및 반환
    return hashTable[hashAddress]
}

// 해시 테이블이 잘 작동하는지 확인

updateValue("루트", forKey: "그")
updateValue("톤", forKey: "예")
updateValue("디", forKey: "쥬")

getValue(forKey: "그")
getValue(forKey: "예")
getValue(forKey: "쥬")
```

### 예톤

```swift
var hashTable = [String?](repeating: nil, count: 3)

func hash(key: Int) -> Int {
    return key % 3 // 51060 % 3 == 0
}
func updateValue(_ value: String, forKey key: String) {
    guard let key = UnicodeScalar(key)?.value else { return }
    print("\(key) key입니돠") // 51060
    let hashAddress = hash(key: Int(key))
    hashTable[hashAddress] = value // hashTable의 0번째 index에 "예톤"이 저장
}
func getValue(forKey key: String) -> String? {
    guard let key = UnicodeScalar(key)?.value else { return nil }
    let hashAddress = hash(key: Int(key))
    return hashTable[hashAddress]
}

updateValue("예톤", forKey: "이")
getValue(forKey: "이")
```
