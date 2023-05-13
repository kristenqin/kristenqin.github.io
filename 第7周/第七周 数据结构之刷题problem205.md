第二个结构体的定义目的是什么 能否从生活中的应用案例进行解释 

```cpp
typedef struct 
{
	string no;
	string name;
	double price;
}Book;

typedef struct
{
	Book *elem;
	int num;
}SqList;
```

第二个结构体的定义是用于实现一个基于顺序表的书籍列表，其中每个元素都是一个 `Book` 结构体类型。 `SqList` 结构体包含一个指向 `Book` 结构体数组的指针 `elem`，以及记录数组中元素个数的整数 `num`。

在生活中，这个结构体可以用于管理一家书店的库存。每本书都有编号、书名和价格等信息，因此可以定义 `Book` 结构体来存储这些信息。而 `SqList` 结构体可以表示整个书店库存，其中每个元素都是一个 `Book` 结构体类型。通过定义 `SqList` 结构体，可以方便地对书店库存进行查询、添加、删除和修改等操作，从而实现更高效的库存管理。