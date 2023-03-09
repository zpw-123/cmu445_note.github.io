# project2.3 b+tree    

Task2 B+Tree Data Structure (Insertion, Deletion, Point Search)   
 
Task2 是单线程B+tree的重点    
*最简单的就是Point Search 首先会先Findleaf() 在查找child page的时候可以进行二分搜索 因为array里面存放的是key 和 value
其中value只是一个 page_id 所以还需要   
![image](https://user-images.githubusercontent.com/60247486/223687880-0765bcd5-7166-4d24-95a7-c8d963f25546.png)   
来获得指向对应 leaf page的指针。  
*还有就是新建一个page的时候，也是需要使用 buffer pool的NewPage() 然后进行类型转换       
![image](https://user-images.githubusercontent.com/60247486/223689090-d99f42bb-97cb-4e46-8ae9-d2011269b67e.png)    
找到eaf page 也是可以进行二分查找 找到key对应的 record id  
*Insert 跟search相同 第一步也是根据key来查找到需要插入的leaf page 然后将key插入到leaf page里面    
但是在插入之后 要考虑是否等于maxsize 然后进行一次leaf page分裂操作    
![image](https://user-images.githubusercontent.com/60247486/223691563-ecc40a7f-8d82-4efa-bb8d-39cf089e93d8.png)    
给parent page插入一个key是因为 这个parent page多了一个子节点    
上面第四步 是重点 因为很有可能 parent page也产生了分裂    

![image](https://user-images.githubusercontent.com/60247486/223692339-8ca2261b-6f9a-44cd-a282-bd724e73abe5.png)    
![image](https://user-images.githubusercontent.com/60247486/223694752-53cce27f-59e8-46ca-9b0e-445d9295cf20.png)     
![image](https://user-images.githubusercontent.com/60247486/223695157-18368e63-9f18-43e3-bc9e-dce47251713c.png)    
########search或者insert都是在 /src/storage/index/b_plus_tree.cpp 里面  
########函数 IsEmpty() 直接查询根节点是否存在就可以   
########函数 GetValue(const KeyType &key, std::vector<ValueType> *result, Transaction *transaction) 首先先找到leaf_page 然后将在leaf_page里面进行二分搜索对应的key 然后注意当FetchPage的时候需要 在Fetch之后 要 使用bufferpoolmanager->UnpinPage   
########函数 Insert(const KeyType &key, const ValueType &value, Transaction *transaction)      
########函数 StartNewTree(const KeyType &key, const ValueType &value) 当插入(key,value)进入empty空的tree的时候 1.首先向缓冲池申请一个新的root page。2对于类中的变量 root_page_id进行赋值 并且更新UpdateRootPageId(1)




