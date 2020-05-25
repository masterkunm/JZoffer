# **面试题22. 链表中倒数第k个节点**

## **Link**

<<https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof>

## **题目描述**

$^1$ 输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。

### 示例

```bash
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.
```

## **题目解析**

* 暴力破解 (O(n+n) = O(n), O(1))
  * 第一反应我们可以想到既然要倒数k个节点，那么我们遍历多少个节点能到呢，当然是遍历n - k个节点后才到我们需要返回的节点；
  * 那这个解法非常简单，首先先遍历一遍真个链表，得到长度n，然后再遍历n - k遍，然后返回该节点；
  * 但是该解法不是最简单的
* 一遍遍历 (O(n), O(1))
  * 既然我们知道要遍历n - k遍才到达我们要的节点，能不能不求n就这么做呢？当然可以，我们使用两个指针，第一个指针先遍历到第k个节点，这个时候第k个节点到结尾就是n - k了，然后两个指针同时往后移动，直到第一个指针到达结尾，第二个指针就移动了n - k遍了；
  * 但是这种做法要求要处理特殊输入：
    * 输入的指针为空
    * k的数值大于链表的长度
    * k的值为零（尤其是如果k的类型为无符号整数，要特别小心）

## **题解**

>C++

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        if (head == nullptr || k == 0) {
            return nullptr;
        }

        ListNode *lastK = head;
        ListNode *curr = head;
        int indexK = 1;
        while (indexK < k && lastK != nullptr) {
            lastK = lastK->next;
            indexK++;
        }

        // k is bigger than the length of the list
        if (lastK == nullptr) {
            return nullptr;
        }

        while (lastK->next != nullptr) {
            lastK = lastK->next;
            curr = curr->next;
        }

        return curr;
    }
};
```

## **reference**

$^1$ 来源：力扣（LeetCode）
链接：<https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof>
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
