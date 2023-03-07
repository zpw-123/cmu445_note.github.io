# cmu445_note.github.io
B+tree在Bustub里面的位置
![image](https://user-images.githubusercontent.com/60247486/223350172-adfc7d1a-5be6-41d4-bded-d208a944d994.png)

*B_PLUS_TREE_INTERNAL_PAGE B+树内页
![image](https://user-images.githubusercontent.com/60247486/223350789-4317e706-d958-4070-a98d-122f70e76ef5.png)

**函数CopyLastFrom  参数·(const MappingType &pair, BufferPoolManager *buffer_pool_manager)
  将pair放到array的最后，需要bufferPoolManager来修改一下子节点的parent_id
  ![image](https://user-images.githubusercontent.com/60247486/223351191-d80a7c4e-4ca3-4037-b9a6-25ee602775b0.png)
  上面四行是经典操作   
**函数MoveLastToFrontOf 参数(BPlusTreeInternalPage *recipient, const KeyType &middle_key,BufferPoolManager *buffer_pool_manager)
  ![image](https://user-images.githubusercontent.com/60247486/223351635-dc48fde9-23b0-4289-8874-f8570d92df52.png)
   
