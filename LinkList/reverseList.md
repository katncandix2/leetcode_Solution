# [反转链表](https://leetcode.com/problems/reverse-linked-list/)

作为笔试经典例题反转链表主要考察对于【链表】以及【指针】的掌握程度


题目的解决方式一眼就可以看出


然而实际的编码过程可能会出现这样或那样的错误导致无法ac


以这一题为例我们将解题分为三个步骤


### 1.读懂题目


Input: 1->2->3->4->5->NULL


Output: 5->4->3->2->1->NULL

我们通过读题知道我们需要返回一个链表的【逆序】

并根据题目描述得知我们的预期输出应是【反转链表后】的头指针


### 2.确定思路
很多笔试的时候我们都会犯一个很大的错误

【一上来就写】

其实更好的做法是树立如何解决

以这一题为例

1.如果链表只有一个元素或者没有元素 我们直接返回即可
2.当链表有一个以上的元素,我们就需要进行如下操作
	
	1.记录当前节点的下一节点
	2.将当前节点指向前一个节点
	3.将我们的游标指向下一节点直到下一节点为空
	
	
### 3.code and debug

	ListNode* reverseList(ListNode* head) {
		  
		  	
        if(head == nullptr ||head->next == nullptr){
		    return head;
	     }
		  
		 //pre 用于让当前指针指向前一个节点 next 用于记录当前指针的下一个节点 
        ListNode *pre = nullptr;
        ListNode *next = nullptr;
        while(head!=nullptr){
            //当前节点第下一节点先存储下来
            next = head->next;

            //当前节点指向上一节点
            head->next = pre;
            //pre 指向当前节点
            pre = head;
            head = next;
        }

        return pre;
    }
   