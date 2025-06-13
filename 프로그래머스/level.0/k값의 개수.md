# k값의 개수

1부터 13까지의 수에서, 1은 1, 10, 11, 12, 13 이렇게 총 6번 등장합니다.

정수 i, j, k가 매개변수로 주어질 때, i부터 j까지 k가 몇 번 등장하는지 return 하도록 solution 함수를 완성해주세요.

### 제한사항
```
    1 ≤ i < j ≤ 100,000
    0 ≤ k ≤ 9
```

## 풀이

이 문제를 풀지 못하였다. 처음부터 정수형으로 자리수를 /, % 을 통해 뽑아내고 k 값과 일치하면 count++ 를 통해 진행했는데

상당히 복잡하고 천의 자리부터 계산이 복잡해지고 시간이 엄청 오래 걸렸다.

### 정수형 -> 문자열

정수형 계산이 필요한게 아닌 존재 여부를 따지므로 문자열로 변경 후 풀면 굉장히 편하다.

```
class Solution {
    fun solution(i: Int, j: Int, k: Int): Int {
        
        var count = 0
        val kstr = k.toString()
        
        for(index in i..j) {
            
            count += index.toString().count {it == kstr[0]}
        }
        return count
    }
}
```
이렇게 문자열로 바꾸고 count{it == kstr[0]} 을 통해 해당 문자열에 k가 존재하면 count값을 1 더해주는 식이다. (count 함수에 대해 알게됐다.)

이를 더 간편히 바꾸면

```
class Solution {
    fun solution(i: Int, j: Int, k: Int): Int = 
        (i..j).joinToString("").count { it.digitToInt() == k }
}
```
i..j의 범위를 만들고 joinToString으로 해당 범위의 값을 하나로 합치는데 String으로 합친다. ("")은 빈칸 없이 붙인다.

그리고 count를 이용하여 문자를 세는데 it.digitToInt()를 통해 문자열을 int 형으로 바꾼 후 k와 비교하여 몇개인지 count 한다.

참 편리하다...

