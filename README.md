# 题目名称二 基于线性表的图书管理系统(链式存储结构)

## 2.1问题描述

该图书管理系统采用链式存储结构来存储图书的书号，因其动态分配内存的特点，管理系统更倾向于用链式存储，以便完成人们对图书的需求操作。（与顺序存储结构的图书管理系统唯一不同就是链式存储而已）

使用语言：C++语言。

编译环境：codeblocks17.12。

## 2.2需求分析

该需求分析与顺序表存储结构的图书管理系统一样，这里不过多介绍

## 2.3概要设计

为了实现需求分析中的功能，可以从3个方面入手

1.主界面设计

为实现图书管理系统各功能，设计一个含有多个菜单的程序以控制各项子功能。
![](https://github.com/0759LW/Library/raw/master/image/图一.png)

2存储结构设计

 本系统采用链式存储的方式来存储图书信息，每个图书信息由书号，书名，价格，还有指向该结构体的指针四个要素组成。此外还设计一个number全局变量，用来检测图书链表的长度，减少一些不必要的代码重复时间运行。且设置了文件指针来存放图书信息进入library.txt文件中。

3系统功能设计

本系统设置了8种不同功能，描述如下。

(1)建立图书管理信息，根据你输入要创建的本数来输入多个图书的信息。该功能由create()函数实现。

(2)图书排序功能，本系统有两个排序功能，分别是根据价格高低来进行排序与根据位置来进行逆序排序，分别由Sort()函数与Reverse()函数来实现。

(3)图书信息修改功能，就是根据所有图书大于或小于图书价格平均值来进行提高20%或降低10%,该功能由modify()函数来实现。

(4)图书查找功能，本系统有多个查找功能，分别是查找价格最高图书，与用查找图书一致，要查找的书位置，分别由Most_value()，Search_name()，Search_site()功能来完成。

(5)删除图书信息，根据由用户想出库的相应位置与书号来进行图书信息的删除或者去除系统中重复的图书，分别由Delete()与Remove_same()函数来完成。

(6)图书插入功能，每次只能插入一本相应位置的图书信息，该功能由Insert()函数来完成。

(7)图书显示功能，显示所有图书的信息，该功能由Output()数来完成。

(8)文件读入和输出功能,主要用来把程序的信息经txt文件类型来处理，由cun()函数和read()函数完成

## 2.4详细设计

1.数据类型定义

struct Book {

   char no[20];

   char name[50];

   float price;

};

 

typedef struct LNode {

   Book data;

   struct LNode *next;

} LNode, *LinkList;

2.系统重要子程序详细设计

（1）顺序表建立函数

void Create(LinkList &L) {

  LinkList p=L;

  LinkList q=new LNode;

   cout<<"当输入的书号，书名和价格都为零(0 0 0)时退出该功能"<<endl;

​    cout << "书号         书名        价格：" << '\n';

   cin >> q->data.no >> q->data.name >> q->data.price;

   while (q->data.no != "0"&& q->data.name != "0"&& q->data.price != 0) {

​       q->next = p->next;

​       p->next = q;

​       p = q;

​       q = new LNode;

​       cin >> q->data.no >> q->data.name >> q->data.price;

​       number++;

   }

   cout<<"图书信息创建完毕，一共有"<<number<<"本书"<<endl;

   output(L);

   cout << endl;

}

## 2.6测试分析

1.图书系统的建立（图一）

在主菜单，用户按下1，开始图书系统建立，并输入书号，书名，价格等信息。

2.图书排序功能，用户按下2或4，图书系统开始按价格降序排序或者逆序排序。（图二）

3.图书修改功能，用户按下3，图书信息的价格根据每本书高于或低于平均值来修改（图三）

4.图书查找功能，用户按下5,6或7，就能根据图书价格最高，用户输入的图书信息或者位置来查找图书。（图四）

5.图书插入功能，用户按下8，就能插入新的图书信息。（图五）

6.图书删除信息，用户按下9或10，就能删除用户指定位置的图书或图书系统中重复的图书。（图六）

7.图书显示功能，用户按下11，就能显示所有图书信息。（图七）
![](https://github.com/0759LW/Library/raw/master/image/图一11.png)
![](https://github.com/0759LW/Library/raw/master/image/图一1.png)
![](https://github.com/0759LW/Library/raw/master/image/图二.png)
![](https://github.com/0759LW/Library/raw/master/image/图三.png)
![](https://github.com/0759LW/Library/raw/master/image/图四.png)
![](https://github.com/0759LW/Library/raw/master/image/图五.png)
![](https://github.com/0759LW/Library/raw/master/image/图六.png)
![](https://github.com/0759LW/Library/raw/master/image/图七.png)
