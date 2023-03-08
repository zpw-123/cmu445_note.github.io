# project2.2 b+tree 叶页

Bustub里面所有的B+tree索引，全部都是非聚簇索引（也就是说value是一个指针，然后磁盘存放的数据的顺序跟b+ tree的顺序不一样）
下面实现 叶页面(leaf page) 的cpp和h文件

**函数Init 参数(page_id_t page_id, page_id_t parent_id, int max_size )     
    主要是调用所有的类中 父类中 所有的Set开头的函数，来对于所有的private里面的变量进行赋值    
    
    
**函数Insert 参数(const KeyType &key, const ValueType &value, const KeyComparator &comparator)        
先找到需要插入的下标index 然后将下标后面的数据全部后移 然后插入即可   
但是有个情况 如果插入的key跟插入下标的key相同 if(comparator(KeyAt(insert_index),key) == 0) 
![image](https://user-images.githubusercontent.com/60247486/223430485-297c41a1-54b7-4a6c-8005-c7e21671250a.png)  
不需要进一步操作 当相同时候 直接return GetSize()就行


**函数MoveHalfTo 参数(BPlusTreeLeafPage *recipient)      
由于b+ tree 有个最小size 所以当移动一半的时候 无法移动一半 需要找到GetMinSize() 就是MaxSize的一半   

**函数MoveAllTo  参数(BPlusTreeLeafPage *recipient)  




