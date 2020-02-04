# 题目名称二 基于线性表的图书管理系统(链式存储结构)



**2.1** **问题描述**

该图书管理系统采用链式存储结构来存储图书的书号，因其动态分配内存的特点，管理系统更倾向于用链式存储，以便完成人们对图书的需求操作。（与顺序存储结构的图书管理系统唯一不同就是链式存储而已）



   while (q->data.no != "0"&& q->data.name != "0"&& q->data.price != 0) {

​       q->next = p->next;



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

- [返回](题目名称二 基于线性表的图书管理系统(链式存储结构))

