# A로 B 만들기

문자열 before와 after가 매개변수로 주어질 때, before의 순서를 바꾸어 

after를 만들 수 있으면 1을, 만들 수 없으면 0을 return 하도록 solution 함수를 완성해보세요.

제한사항
```
    0 < before의 길이 == after의 길이 < 1,000
    before와 after는 모두 소문자로 이루어져 있습니다.
```


## 풀이

길이가 같으며 모두 소문자이므로 asc코드로 변경 후 모두 더한 값이 같다면 두 문자열은 배열만 다르지 알파벳은 같다.

```
class Solution {
    fun solution(before: String, after: String): Int {
        var count_1 = 0
        var count_2 = 0
        before.map{it -> it.code}.forEach{count_1 += it}
        after.map{it -> it.code}.forEach{count_2 += it}
        
        return if(count_1 == count_2) 1 else 0
    }
}
```
다른 사람의 풀이를 봤는데 훨씬 간편한 방법이 있다.

문자열을 toList()로 Char이 담긴 list로 변경 후 sorted()를 이용해서 알파벳 순으로 바꾸면 굳이 asc코드를 구하고 더하지 않고

List의 배열이 같다만 판단하면 된다.

```
 class Solution {
    fun solution(before: String, after: String): Int =
      if (before.toList().sorted() == after.toList().sorted()) 1 else 0
}
```
