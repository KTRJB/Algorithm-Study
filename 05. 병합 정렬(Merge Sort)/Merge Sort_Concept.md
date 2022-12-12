### 📍 병합 정렬(Merge Sort)
- 비교 기반 정렬 알고리즘.
- 수열을 하나의 수가 될 때까지 분할을 한 후 다시 병합하는 정렬 방식이다.

![](https://i.imgur.com/Clav1zC.gif)

#### 🔗 구현방법
1. 리스트의 길이가 1 이하라면 이미 정렬된 것으로 본다.
2. 분할(divide): 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.
3. 정복(conquer): 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
4. 결합(combine): 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다. 이때 정렬 결과가 임시배열에 저장된다. <- 실제 정렬이 이뤄지는 구간.
5. 복사(copy): 임시 배열에 저장된 결과를 원래 배열에 복사한다.

![](https://i.imgur.com/z3At868.png)

#### 🔗 장단점
- 장점
    - input의 정렬 정도에 관련없이 어느 정도의 성능을 보장해준다.
- 단점
    - 이미 정렬되어 있는 Input이라도 항상 같은 횟수의 연산을 한다.
    - 별도의 임시 배열이 필요하다.(제자리 정렬 = in-place sorting)이 아니다.
    - 추가적인 Memory가 필요하다.

#### 🔗 시간복잡도 
- 최악 시간복잡도 O(n log n)
- 최선 시간복잡도 O(n log n)
- 평균 시간복잡도 일반적으로, O(n log n)
- 공간복잡도	О(n)

#### 🔗 코드
```swift
import Foundation

func mergeSort(_ value: [Int]) -> [Int] {
    guard value.count > 1 else { return value }
    
    let mid = value.count / 2
    let left = Array(value[0..<mid])
    let right = Array(value[mid..<value.count])
    
    return merge(mergeSort(left), mergeSort(right))
}

func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var left = left
    var right = right
    var result = [Int]()
    
    while !left.isEmpty && !right.isEmpty { // 둘 다 숫자를 가지고 있을 때
        if left.first! < right.first! { // 더 작은 값을 순서대로 넣어준다.
            result.append(left.removeFirst())
        }else {
            result.append(right.removeFirst())
        }
    }
    
    result.append(contentsOf: left+right) // 남은 숫자들을 추가해준다.
    
    return result
}
```
https://ko.wikipedia.org/wiki/%ED%95%A9%EB%B3%91_%EC%A0%95%EB%A0%AC
https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html
https://babbab2.tistory.com/102
