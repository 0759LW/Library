# 题目名称二 基于线性表的图书管理系统(链式存储结构)



**2.1** **问题描述**

该图书管理系统采用链式存储结构来存储图书的书号，因其动态分配内存的特点，管理系统更倾向于用链式存储，以便完成人们对图书的需求操作。（与顺序存储结构的图书管理系统唯一不同就是链式存储而已）

使用语言：C++语言。

编译环境：codeblocks17.12。

**2.2** **需求分析**

该需求分析与顺序表存储结构的图书管理系统一样，这里不过多介绍

**2.3** **概要设计**

为了实现需求分析中的功能，可以从3个方面入手

1.主界面设计

为实现图书管理系统各功能，设计一个含有多个菜单的程序以控制各项子功能。

 

![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image002.png)

 

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

 

 

**2.4** **流程图**

 

 

 

 

 

 

 

 

 



 

 

 

 

 

 

 

 

 

 

 



**2.5** **详细设计**

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

（2）图书去重函数

void Remove_same(LinkList &L) {//图书去重；

 

   LinkList p =L, q,h;

   while (p->next!=NULL) {

​       q = p->next;

​       while (q->next!=NULL) {

​          if (strcmp(p->next->data.no, q->next->data.no) == 0) {

​              h=q->next;

​              q->next = h->next;

​              delete h;

​              number--;

​          }

​          q = q->next;

​          if (q == NULL)

​      {break;}

​       }

​       p = p->next;

   }

   output(L);

}

**2.6** **测试分析**

1.图书系统的建立（图一）

在主菜单，用户按下1，开始图书系统建立，并输入书号，书名，价格等信息。

2.图书排序功能，用户按下2或4，图书系统开始按价格降序排序或者逆序排序。（图二）

3.图书修改功能，用户按下3，图书信息的价格根据每本书高于或低于平均值来修改（图三）

4.图书查找功能，用户按下5,6或7，就能根据图书价格最高，用户输入的图书信息或者位置来查找图书。（图四）

5.图书插入功能，用户按下8，就能插入新的图书信息。（图五）

6.图书删除信息，用户按下9或10，就能删除用户指定位置的图书或图书系统中重复的图书。（图六）

7.图书显示功能，用户按下11，就能显示所有图书信息。（图七）

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image004.png)****（图一）**

 

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image006.png)**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)****（图二）**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image010.png)****（图三）**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image012.png)**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image016.png)****（图四）**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image018.png)****（图五）**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image020.png)**

 

 

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image022.png)****（图六）**

**![img](file:///C:/Users/ADMINI~1/AppData/Local/Temp/msohtmlclip1/01/clip_image024.png)****（图七）**

**2.7** **源程序清单**

\#include<iostream>

\#include<cstring>

\#include<cstdio>

\#include <stdio.h>

\#include<iomanip>

using namespace std;

int flag=0;

int number=0;

struct Book {

​    char no[20];

​    char name[50];

​    float price;

};

 

typedef struct LNode {

​    Book data;

​    struct LNode *next;

} LNode, *LinkList;

 

 

void output(LinkList L) {

​    LinkList p = L->next;

 if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    while (p) {

​        cout << "书号         书名        价格：" << '\n';

​       cout << p->data.no << "\t" << p->data.name << "\t" <<setiosflags(ios::fixed)<<setprecision(2)<<p->data.price<<endl;

​       p = p->next;

​    }

​    cout <<"书的数目为"<<number<<endl;

 

}

 

void Create(LinkList &L) {

​      FILE *fp;

   fp=fopen("library.txt","r+");

   flag=1;

if(fp==NULL)

{

  fp=fopen("library.txt","w+");

 

}

   LinkList p=L;

   LinkList q=new LNode;

​    cout<<"当输入的书号，书名和价格都为零(0 0 0)时退出该功能"<<endl;

​     cout << "书号         书名        价格：" << '\n';

​    cin >> q->data.no >> q->data.name >> q->data.price;

​    while (q->data.no != "0"&& q->data.name != "0"&& q->data.price != 0) {

​       q->next = p->next;

​       p->next = q;

​       p = q;

​       q = new LNode;

​       cin >> q->data.no >> q->data.name >> q->data.price;

​       number++;

​    }

​    cout<<"图书信息创建完毕，一共有"<<number<<"本书"<<endl;

​    output(L);

​    cout << endl;

​    fclose(fp);

}

 

 

 

void Sort(LinkList &L) {//降序输出；

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    LinkList p = L;

​    p = L;

 

​    for (int i = 1; i <= number- 1; i++) {//使用冒泡排序

​       int temp = 0;

​       for (int j = 1; j <= number - i; j++) {

​           LinkList q = p->next->next;

​           if (p->next->next->data.price > p->next->data.price) {

​              p->next->next = q->next;

​              q->next = p->next;

​              p->next = q;

​        temp=1;

​           }

​           p = p->next;

​       }

​      if(temp==0) break;

​      p=L;

​    }

 

​    cout<<"降序操作完成！"<<endl;

​     output(L);

​    cout << endl;

}

 

void Modify(LinkList &L) {//修改图书信息；

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    float count = 0, average,n=0;

​    LinkList p = L->next,q=L->next;

​    while (p) {

​       count += p->data.price;

​       p = p->next;

​       n++;

​    }

​    average = count / n;//求均值

​    while (q) {//修改价格

​       if (q->data.price < average)q->data.price *= 1.2;

​       else q->data.price *= 1.1;

​       q = q->next;

​    }

 

​    cout<<"修改前所有的图书的平均价格为："<<setiosflags(ios::fixed)<<setprecision(2)<<average<<endl;

​    cout<<"修改后的书本价格为"<<endl;

​    output(L);

 

​    cout << endl;

}

 

void Reverse(LinkList &L) {//图书逆序排列；

 cout<<"图书的逆序排列为 ："<<endl;

 if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    LinkList p = L->next;

​    L->next = NULL;

​    while (p) {//使用前插法；

​       LinkList q = p->next;

​       p->next = L->next;

​       L->next = p;

​       p = q;

​    }

 

​     output(L);

​    cout << endl;

}

void Most_value(LinkList &L)

{ int num=0;

  cout<<"下面输出的是价格最贵的图书"<<endl;

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

  LinkList q=new LNode;

  q->data.price=0;

  LinkList p = L->next;

 

​    while (p) {

​       if(q->data.price<p->data.price)

​    {

​      q->data.price=p->data.price;

​    }

​       p = p->next;

​    }

​    p=L->next;

​    while (p) {

​       if(q->data.price==p->data.price)

​    {

​      cout << "书号         书名        价格：" << '\n';

​    cout << p->data.no << "\t" << p->data.name << "\t" <<setiosflags(ios::fixed)<<setprecision(2)<<p->data.price<<endl;

​    num++;}

​       p = p->next;

​    }

​     cout<<"最贵的图书有"<<num<<"本"<<endl;

 

 

 

}

 

void Search_name(LinkList &L) {

  if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    int i;int i1;

​    int n = 0; //记录相同书名图书个数

​    int j,m;

​    char NAME[20][20];

  LinkList p = L->next;

  cout<<"请输入要查找的次数"<<endl;

  cin>>m;

​    cout << "请输入需要查找的"<<m<<"本书名：" ;

​    for(i1=0;i1<m;i1++)

  {

​     cin>>NAME[i1];

  }

​    cout << endl;

for(j=0;j<m;j++){

  while (p) {

​       if((strcmp(p->data.name,NAME[j])) == 0)

​    {

​      cout << "书号      书名       价格：" << endl;

​           cout << p->data.no << "\t" << p->data.name << "\t" << p->data.price << endl;

​           n = n + 1;

​    }

​       p = p->next;

​    }

 

​    if(n==0) {

​       cout << "抱歉,没有你的最爱！" << endl;

​    }

​    else

  {

​    cout<<"已找到"<<n<<"本与你喜爱的书同名的书本"<<endl;

  }

  n=0;

  p=L->next;

}

 

}

 

 

void Search_site(LinkList &L)

{

  if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

 int shu; int i;

​    LinkList p = L, q;

​    int j = 0,m;

​    cout<<"请输入要输出的书本数目："<<endl;

​    cin>>shu;

​    for(i=1;i<=shu;i++){

 

​    cout << "输入要查找的图书位置序号\n";

​    cin >> m;

​    while ((p->next!=NULL) &&(j < m - 1)) {

​       ++j;

​       p = p->next;

​    }

​    if ((p->next ==NULL)|| (j > m - 1))

  {cout << "抱歉，最佳位置上的图书不存在！\n"<<endl;

​    return ;}

 

​    else {

​       p= p->next;

 

 

 

​     cout << "书号         书名        价格：" << '\n';

​    cout << p->data.no << "\t" << p->data.name << "\t" <<setiosflags(ios::fixed)<<setprecision(2)<<p->data.price<<endl;

 

​    }

j = 0;

p=L;

}

​    cout << endl;

 

}

 

 

 

void Insert(LinkList &L) {//插入新图书；

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    LinkList p=L,q = new LNode;

​    int j = 0, m;

​    cout << "输入入库图书的位置\n";

​    cin >> m;

​    cout << "输入新书的 书号 书名 价格\n";

​    cin >> q->data.no >> q->data.name >> q->data.price;

​    while ((p !=NULL)&&(j < m-1)) {//定位；

​       ++j;

​       p = p->next;

​    }

​    if ((p==NULL)||(j>m-1))

  {cout << "抱歉，入库位置非法\n";return ;}

​    else {

​       q->next = p->next;

​       p->next = q;

​       p = L->next;

​    }

​    number++;

​    output(L);

 

​    cout << endl;

}

 

void Delete(LinkList &L) {//删除旧图书；

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    LinkList p = L, q;

​    int j = 0,m;

​    cout << "输入要删除的图书序号\n";

​    cin >> m;

​    while ((p->next!=NULL) &&(j < m - 1)) {

​       ++j;

​       p = p->next;

​    }

​    if ((p->next ==NULL)|| (j > m - 1))

  {cout << "抱歉，出库位置非法\n";return ;}

 

​    else {

​       q = p->next;

​       p->next = q->next ;

​       delete q;

 

​    }

​    number--;

​    output(L);

​    cout << endl;

}

 

void Remove_same(LinkList &L) {//图书去重；

if(flag==0) {

​       cout << "还未创建图书！" << endl;

​       return;

​    }

​    LinkList p =L, q,h;

​    while (p->next!=NULL) {

​       q = p->next;

​       while (q->next!=NULL) {

​           if (strcmp(p->next->data.no, q->next->data.no) == 0) {

​              h=q->next;

​              q->next = h->next;

​              delete h;

​              number--;

​           }

​           q = q->next;

​           if (q == NULL)

​      {break;}

​       }

​       p = p->next;

​    }

​    output(L);

}

void menu()

{

  cout << "********************************图书信息管理系统（链式存储结构）*******************************" << endl;

​       cout << "      |      欢迎进入图书管理系统~!      |" << endl;

​       cout << "      |                       |" << endl;

​       cout << "      |      请输入数字选择服务：       |" << endl;

​       cout << "      |      1.图书信息的创建         |" << endl;

​       cout << "      |      2.图书信息的排序(降序)      |" << endl;

​       cout << "      |      3.图书信息的修改         |" << endl;

​       cout << "      |      4.图书信息的逆序         |" << endl;

​       cout << "      |      5.最贵图书的查找         |" << endl;

​       cout << "      |      6.最爱图书的查找         |" << endl;

​       cout << "      |      7.最佳位置图书的查找       |" << endl;

​       cout << "      |      8.新图书的入库          |" << endl;

​       cout << "      |      9.旧图书的出库          |" << endl;

​       cout << "      |      10.图书信息的去重        |" << endl;

​       cout << "      |      11.图书信息的显示        |" << endl;

​       cout << "      |      0.保存数据并退出系统            |" << endl;

​       cout << "***********************************************************************" << endl << endl;

}

 

void cun(LinkList L,FILE *fp)

{

  LinkList p1=new LNode;

 

 

  p1 = L;/*使p1指向主程序的head*/

  p1 = p1->next;/*该程序是head的后继指针指向下一个结点，head指针不用来存储结构体*/

  while(p1 != NULL)/*以链表形式将程序里的数据输出到文件里，遍历进行*/

  {

​    number--;

​    fprintf(fp,"%s %s %f\n",p1->data.no, p1->data.name ,p1->data.price);

​    p1 = p1->next;

  }

 

 

  return;

}

void read(LinkList L,FILE *fp)

{/*如果该文件存在，才执行这个函数*/

number=0;

  LinkList p,r;

   r=L;/*使r指向主程序的head*/

   p=new LNode;

   while( fscanf(fp,"%s %s %f ",p->data.no, p->data.name ,&(p->data.price))!=EOF)/*读到eof结束*/

   { /*这里就是使数据里的数据形成链表读入到程序里，以head为头指针*/

​     r->next=p;

​      r=p;

​      p=new LNode;

​      /*动态申请一个空间，用来存放一个结点，并用临时指针p指向这个结点*/

​      number++;

   }

   r->next=NULL;

​    flag=1;

 

}

int main() {

 

 LinkList L;

​    L = new LNode;

​    L->next = NULL;

 FILE *fp;/*创建文件指针*/

 fp=fopen("library.txt","r+");

  if(fp!=NULL) /*若存在librarye.txt这个文件，就调用read这里函数将文件里的数据输入到程序里*/

{ cout<<"已存在对应的图书信息文件，已把文件里的信息输入程序中了\n"<<endl;

  read(L,fp);

  fp = fopen("library.txt","w+");}

​    int n;

​    while(1) {

​     menu();

​    cin>>n;

​       switch (n) {

​       case 1:Create(L); break;

​       case 2:Sort(L); break;

​       case 3:Modify(L); break;

​       case 4:Reverse(L); break;

​       case 5:Most_value(L);break;

​       case 6:Search_name(L);break;

​       case 7:Search_site(L);break;

​       case 8:Insert(L); break;

​       case 9:Delete(L); break;

​       case 10:Remove_same(L); break;

​       case 11:output(L);break;

​       case 0 :cun(L,fp);cout<<"谢谢你的使用"<<endl;return 0;

​       default:cout << "请选择正确的操作！！！"<<endl;break;

​       }

}

​    return 0;

}

**题目名称三 基于二叉树的表达式求值算法**

**3.1****问题描述**

输入一个表达式（表达式中的数为整数），利用二叉树来表示该表达式，创建表达式树，然后利用二叉树的遍历操作求表达式的值。

使用语言：C++语言。

编译环境：codeblocks17.12

**3.2****需求分析**

(1)能够输入多组数据。每组数据1行，为一个表达式，表达式以“=”结尾。当输入只有一个“=”时，输入结束。

(2)每组数据输出1行，为表达式的值。

**3.3****概要设计**

为了实现需求分析中的功能，可从三个方面入手。

\1. 界面设计

为实现表达式求值算法，设计一个简单的菜单来控制该功能。并在第一次进入程序时，会显示相应的程序说明。如下图：

- [返回](#题目名称二 基于线性表的图书管理系统(链式存储结构))
