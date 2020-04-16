# **字符串归一化**

## **Link**

https://www.nowcoder.com/practice/6d5e036defdf408681376a4a9d4930ff?tpId=98&tqId=32844&tPage=2&rp=2&ru=/ta/2019test&qru=/ta/2019test/question-ranking

## **题目描述**

通过键盘输入一串小写字母(a~z)组成的字符串。
请编写一个字符串归一化程序，统计字符串中相同字符出现的次数，并按字典序输出字符及其出现次数。
例如字符串"babcc"归一化后为"a1b2c2"

### 输入描述:

```bash
每个测试用例每行为一个字符串，以'\n'结尾，例如cccddecca
```

### 输出描述:

```bash
输出压缩后的字符串ac5d2e
```

## **题目分析**

一开始我的第一反应是使用hashmap/hashtable的，但是由于英文char的实际字符数量只有26个，所以比较方便的做法是用一个size为26的array。

1. count[26] = {0}; 初始化均为0；

2. count[i - 'a'] += 1; 对应的char位置为char - 'a'（根据ascii表）;

3. 输出非零的char以及相应的count；

## **解题**

```cpp
#include <stdio.h>

int main() {
    // array for 26 chars, each count init as 0;
    int count[26] = {0};

    char c;
    // stdin -> char -> count this char into array
    while ( ( c = getchar() ) != '\n') {
        count[c-'a'] += 1;
    }

    // output the non-zero char and its count
    for (int i = 0; i < 26; i++) {
        if (count[i]) printf("%c%d", 'a'+i, count[i]);
    }

    putchar('\n');

    return 0;
}
```
