算法库
====
　　
## std::adjacent_find

### 模板声明
1. 默认
	```C++
	template <class ForwardIterator>
	ForwardIterator adjacent_find (ForwardIterator first, ForwardIterator last);
	```
2. 常用
	```C++
	template <class ForwardIterator, class BinaryPredicate>
	ForwardIterator adjacent_find (ForwardIteratofirst, ForwardIterator last,
	BinaryPredicate pred);
	```
### 功能
查找一个序列中是否存在指定元素。  
如果在[first,last)中存在任何值与val相等，返回`true`，否则返回`false`。


### 实现代码
	```C++
    template <class ForwardIterator>
    ForwardIterator adjacent_find (ForwardIterator first, ForwardIterator last)
    {
      if (first != last)
      {
      		ForwardIterator next=first; ++next;
      		while (next != last) {
      		if (*first == *next) // or: if (pred(*first,*next)), for version (2)
    			return first;
      		++first; ++next;
    	}
      }
      return last;
    }
 	```

### 参数说明
**first,last：**  
迭代器规定了访问序列，范围在[first,last)，包括第一个元素，但是不包括最后一个元素。

**pred：**  
二进制函数，接受两个元素作为参数，并返回一个可转换为bool的值。返回的值表示是否在上下文中匹配。此函数不能修改任何参数，既可以是指针，也可以是函数对象。  

### 返回值
返回指向第一个匹配元素的迭代器，比如{1,2,3,4,5}如果要找3的话，返回值就是指向3的一个迭代器。如果没有找到，那么返回最后一个元素，在这里就是返回5。  

### 代码

