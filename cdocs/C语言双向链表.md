双向链表是每个结点都有两个指针域，一个**Next**和**Prev**。结构体定义如下：

```c
struct DList {
    int num;
    struct DList *Next;
    struct DList *Prev;
};
```

## 头结点

双链表的头结点和单链表的头结点类似，头结点都不存储数据。头结点的'Prev'为NULL，Next为NULL或指向第一个结点。

### 创建头结点

