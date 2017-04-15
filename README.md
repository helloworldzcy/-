#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <math.h>
#include "malloc.h"
#include "windows.h"

struct book
{
    char number[7];//注意不能为6；
    char name[40];
    char writer[20];
    char publisher[50];
    char date[10];
    double price;
    int stock;
    struct book *next;
};

struct book *head;

void login();
void book_display();
void meun();
void Change_surface();
void Change(char k);
void Sta_surface();
void book_publisher();
void book_writer();
void book_stock();
void Del_message(int n);
void Del_surface();
void Delect_book();
void Input_surface();
void Input_newbook();
void Search_surface();
void Search_book(char ch);

void create()
{
    int a=1000;
    struct book *p=NULL,*q=NULL;
    head=NULL;
    FILE *fp;
    fp=fopen("books.txt","r");
    if(fp==NULL)
    {
        printf("打开文件失败！");
        Sleep(a);
        system("cls");
        meun();
    }
    else
    {
      p=(struct book *)malloc(sizeof(struct book));
      while(fscanf(fp,"%s %s %s %s %s %lf %d\n",p->number,p->name,p->writer,p->publisher,p->date,&p->price,&p->stock)!=EOF)
      {
        p->next=NULL;
        if(head==NULL)
        head=p;
        else
        {
            q->next=p;
        }
        q=p;
        p=(struct book *)malloc(sizeof(struct book));
      }
    }
    fclose(fp);
}

void write_message()
{
    struct book *p;
    p=head;
    FILE *fp;
    int a=1000;
    fp=fopen("books.txt","w");
    if(fp==NULL)
    {
        printf("\n\n\n                       打开文件失败！\n\n");
        printf("                  系统将自动返回主菜单，请等待...\n");
        Sleep(a);
        system("cls");
        meun();
    }
    else
    {
    while(p!=NULL)
    {
    fprintf(fp,"%s %s %s %s %s %.2f %d\n",p->number,p->name,p->writer,p->publisher,p->date,p->price,p->stock);
    p=p->next;
    }
    }
    fclose(fp);
}


int main()
{
    login();
    struct book *head;
    create();
    meun();
}

void login()
{
    int a=2000;
    char ch[10];
    printf("                          +                                     +\n");
    printf("                                 +             +                     \n");
    printf("                      +                                 +\n");
    printf("                                  +                      \n");
    printf("      +                +        〓〓〓〓   〓〓〓〓          +      \n");
    printf("                 +              〓         〓            +                +      \n");
    printf("      +            〓〓〓〓        迎         来    +  〓〓〓〓   +           +\n");
    printf("                   〓                 〓         〓    〓\n");
    printf("                      欢        〓〓〓〓   〓〓〓〓       到    + \n");
    printf("         +               〓    +                     +       〓             +\n");
    printf("                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +           +                          〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n\n\n");
    printf("                 +                   ◆请登录               +\n\n");
    printf("                                    +温馨提示+                    +\n\n");
    printf("                                输入0,进入登录界面\n\n");
    printf("                                请输入：");
    scanf("%s",ch);
    while(ch[1]!='\0'||ch[0]!='0')
    {
        printf("\n                                输入有误，请重新输入！\n\n");
        printf("                                请输入：");
        scanf("%s",ch);
    }
        if(ch[0]=='0')
    {
        system("cls");
    char id[20]="201625010429",password[16]="20161219";
    char id1[20],password1[16];
    char ch1;
    printf("                                     +                            +\n");
    printf("                                 +       +      +                    + \n");
    printf("          +            +                                 +                   + \n");
    printf("                                  +            +             +            +\n");
    printf("    +          +         +         账号:");
    scanf("%s",id1);
    while(strcmp(id,id1)!=0)//验证用户名是否存在，不存在则重新输入；
    {
        printf("\n                          该用户不存在，请重新输入\n");
        Sleep(a);
        system("cls");
            printf("                          +                                     +\n");
        printf("                                 +             +                     \n");
        printf("                      +                                 +\n");
        printf("                                  +                      \n");
        printf("\n    +          +         +         账号:");
        scanf("%s",id1);
    }
    if(strcmp(id1,id)==0)
    {
        printf("\n  +              +                 密码:");
        scanf("%s",password1);
        while(strcmp(password,password1)!=0)
        {
            printf("\n    +            +                 密码错误,请重新输入  +                      +\n");
            printf("                             +                  +                   +\n");
            printf("    +                    +         密码:");
            scanf("%s",password1);
        }
        if(strcmp(password,password1)==0)
        {
        printf("                                     +                            +\n");
        printf("                                 +       +      +                    + \n");
        printf("          +            +                                 +                   + \n");
        printf("                                  +            +             +            +\n");
        Sleep(a);
           system("cls");
        }
    }
    }
}

void meun()
{
    int n,flag=1,a=1000;
    struct book *newbook;
    printf("\n\n\n\n                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +           +                          〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n\n\n");
    printf("                   _________________Please choose!__________________\n\n");
    printf("      +                             1.遍历图书\n");
    printf("                       +                            +               +\n");
    printf("         +                          2.修改图书信息\n");
    printf("                                  +                            +               +\n");
    printf("                +                   3.统计图书\n");
    printf("        +                            +               +        \n");
    printf("                              +     4.删除图书\n");
    printf("                      +                +               +        \n");
    printf("                                    5.查找图书\n");
    printf("              +                       +                            +               +        \n");
    printf("                                    6.新增图书\n");
    printf("            +                                                 +\n");
    printf("                                    7.退出系统\n");
    printf("            +                     +                            +\n");
    while(flag==1)
    {
    printf("                                请选择要操作的序号:");
    scanf("%d",&n);getchar();
    system("cls");
    switch(n)
    {
        case 1:
               flag=0;
               create();
               printf("温馨提示：下一步：返回主菜单\n");
               book_display();
               system("pause");
               system("cls");
               meun();
               break;
        case 2:flag=0;
               create();
               Change_surface();
               break;
        case 3:flag=0;
               create();
               Sta_surface();
               break;
        case 4:flag=0;
               create();
               Del_surface();
               break;
        case 5:flag=0;
               create();
               Search_surface();
               break;
        case 6:flag=0;
               create();
               Input_surface();
               break;
        case 7:flag=0;system("cls");break;
        default:printf("\n\n\n\n                          输入有误，请重新输入!\n");
                Sleep(a);
                system("cls");
                meun();
    }
    }
}

void book_display()
{
    struct book *p;
    p=head;
    printf("\n         ISBN码    书名              作者        出版社           出版日期     价格      库存 \n\n");
    while(p!=NULL)
    {
        printf("         %-8s %-18s %-10s %-20s %-8s %-6.2f元   %-2d本\n\n",p->number,p->name,p->writer,p->publisher,p->date,p->price,p->stock);
        p=p->next;
    }
}

void Change_surface()
{
    int a=1000,flag=0;
    char b[10];
    printf("\n\n\n\n                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +           +                          〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n\n\n");
    printf("                   _________________Please choose!__________________\n\n");
    printf("         +                1.修改图书信息         2.返回主菜单\n");
    printf("+                         +               +                          +\n");
    printf("                    +                +                  +\n");
    printf("       +                   +       请选择操作序号：");//还没写完呢
    scanf("%s",b);
    while(b[1]!='\0'||b[0]<'1'||b[0]>'2')
    {
        flag=1;
        printf("\n       +                   +       输入有误，请重新输入\n\n");
        printf("                                   请等待...\n\n");
        Sleep(a);
        system("cls");
        Change_surface();
    }
    if(flag==0)
    {
    if(b[0]=='1')
        Change(b[0]);
    else
    {
        system("cls");
        meun();
    }
    }

}
void Change(char k)//修改图书信息
{
    struct book *p;
    int i,j,stock,a=2000,flag=0,len,t=0,w=0;
    char s[7],name[30],writer[20],publisher[50],date[10],ch[10],choice[10],b[10],c[10];
    double price;
    p=head;
     if(head==NULL)
     {
        printf("                                   该书库为空！\n\n");
        system("pause");
        system("cls");
        meun();
     }
     system("cls");
    printf("\n                             请输入图书的ISBN号:");
    scanf("%s",s);
    len=strlen(s);
    while(len!=6||s[1]!='-'||s[0]<'A'||s[0]>'V')
    {
        printf("\n                     输入编号形式有误，请按照规定形式输入编号！\n\n");
        printf("                     ◆重新输入请输入Y，返回上一页请输入N\n\n");
        printf("                     请输入:");
        scanf("%s",c);
        while(c[1]!='\0')
       {
              printf("\n                     输入有误，请重新输入\n");
              printf("\n                     请输入:");
              scanf("%s",c);
       }
       while(c[0]!='Y'&&c[0]!='N')
       {
              printf("\n                     输入有误，请重新输入\n");
              printf("\n                     请输入:");
              scanf("%s",c);
       }
        if(c[0]=='Y')
        {
                printf("\n\n                             请输入图书的ISBN号:");
                scanf("%s",s);
                len=strlen(s);
        }
        else
        {
              t=1;
              system("cls");
              Change_surface();
              break;
        }
    }
    if(t==0)
    {
    while(p!=NULL)
    {
         j=strcmp(p->number,s);
         if(j==0)
         {
            flag=1;
            printf("\n       +              +             ⊙0⊙找到了！  +\n");
            printf("                                     +                            +\n");
            printf("                                 +       +      +                    + \n");
            printf("                      +                                 +                   + \n");
            printf("                                  +            +             +            +\n");
            printf("            +                +     ISBN码：");
            printf("%s\n\n",p->number);
            printf("     +                      +      书名：");
            printf("%s\n\n",p->name);
            printf("                   +              +作者：");
            printf("%s\n\n",p->writer);
            printf("                 +                 出版社：");
            printf("%s       +           +\n\n",p->publisher);
            printf("                           +       出版日期：");
            printf("%s  +                        +\n\n",p->date);
            printf("      +                            价格：");
            printf("%.2f 元        +\n\n",p->price);
            printf("                           +       库存：");
            printf("%d 本\n\n",p->stock);
            printf("       +                ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
            printf("                        1.修改书名     +      5.修改价格  +                        +\n\n");
            printf("            +           2.修改作者            6.修改图书库存   +               +\n\n");
            printf("                        3.修改出版社      +   7.修改以上所有信息           +            +\n\n");
            printf("    +                   4.修改出版日期        8.取消,返回上一页                   +\n\n");
            printf("                        ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆            +           +\n\n");
            printf("                   +       请输入你要选择的操作编号:");
            scanf("%s",choice);
            while(choice[1]!='\0'||choice[0]<'1'||choice[0]>'8')
            {
                   printf("\n                           输入有误，请重新输入\n");
                   printf("\n                           请输入你要选择的操作编号:");
                   scanf("%s",choice);
            }
            switch(choice[0])
            {
                case'1':printf("\n\n                           请输入书名：");
                         scanf("%s",name);
                         strcpy(p->name,name);
                         break;
                case'2':printf("\n\n                           请输入作者：");
                         scanf("%s",writer);
                         strcpy(p->writer,writer);
                         break;
                case'3':printf("\n\n                           请输入出版社：");
                         scanf("%s",publisher);
                         strcpy(p->publisher,publisher);
                         break;
                case'4':printf("\n\n                           请输入出版日期：");
                         scanf("%s",date);
                         strcpy(p->date,date);
                         break;
                case'5':printf("\n\n                           请输入书本价格(如 20.00)：");
                         scanf("%lf",&price);
                         p->price=price;
                         break;
                case'6':printf("\n\n                           请输入书本库存（如 3）：");
                         scanf("%d",&stock);
                         p->stock=stock;
                         break;
                case'7': printf("\n\n                           请输入书名：");
                         scanf("%s",name);
                         printf("\n\n                           请输入作者：");
                         scanf("%s",writer);
                         printf("\n\n                           请输入出版社：");
                         scanf("%s",publisher);
                         printf("\n\n                           请输入出版日期：");
                         scanf("%s",date);
                         printf("\n\n                           请输入书本价格(如 20.00)：");
                         scanf("%lf",&price);
                         printf("\n\n                           请输入书本库存（如 3）：");
                         scanf("%d",&stock);
                         strcpy(p->name,name);
                         strcpy(p->writer,writer);
                         strcpy(p->publisher,publisher);
                         strcpy(p->date,date);
                         p->price=price;
                         p->stock=stock;
                         break;
               case'8':
                       w=1;
                       system("cls");
                       Change_surface();
                       break;
              default:w=1;
                      printf("\n                           输入有误,请重新输入！\n");
                      Sleep(a);
                      system("cls");
                      Change(k);
            }
            if(w==0)
            {
            write_message();
            printf("\n\n                                  √修改成功\n");
            Sleep(a);
            system("cls");
            printf("                                     +                   +         +\n");
            printf("                                 +       +      +                    + \n");
            printf("                      +                                 +                   + \n");
            printf("                                  +            +             +            +\n");
            printf("\n          +            是否继续图书信息更改!继续请输入Y           +        \n");
            printf("\n                    +       返回上一页请输入N       +                   +    +\n");
            printf("\n          +        +        请输入：");
            scanf("%s",ch);
            while(ch[1]!='\0')
            {
                   printf("                      +                                 +                   + \n");
                   printf("                           输入有误，请重新输入\n");
                   printf("\n                           请输入:");
                   scanf("%s",ch);
            }
            while(ch[0]!='Y'&&ch[0]!='N')
            {
                   printf("\n                           输入有误，请重新输入\n");
                   printf("\n                           请输入:");
                   scanf("%s",ch);
            }
            if(ch[0]=='Y')
            {
                system("cls");
                Change(k);
            }
            else
            {
                system("cls");
                Change_surface();
            }
                        break;
         }
         }
         p=p->next;
    }
    if(flag==0)
    {
            printf("\n                           馆内暂无此书！\n");
            printf("\n                           请等待系统自动跳转回上一页面\n");
            Sleep(a);
            system("cls");
            Change_surface();
     }
    }
}

void Sta_surface()
{
    int i,a=1000;
    char ch[10],c[10];
    printf("\n\n\n\n                        〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                       〓        +         +              \n");
    printf("                                 +      图书管理系统            +       \n");
    printf("        +           +                               〓            \n");
    printf("                            +         〓〓〓〓〓〓〓〓    +        +                 \n\n\n");
    printf("      +                         ■■■■■■信息统计■■■■■■\n\n");
    printf("                               |------------|     |------------|        +       \n");
    printf("                     +         |1.统计信息  |  +  | 2.主菜单   |                   +\n");
    printf("         +                     |------------|     |------------|         +            \n\n");
    printf("                               +                   +                  +              +\n ");
    printf("     +                             +  请输入你的选择：");
    scanf("%s",ch);
    while(ch[1]!='\0')
    {

        printf("\n                               输入有误，请重新输入！\n\n");
        printf("\n                                      请输入你的选择：");
        scanf("%s",ch);
    }
     while(ch[0]<'1'||ch[0]>'2')
    {

        printf("\n                               输入有误，请重新输入！\n\n");
        printf("\n                                      请输入你的选择：");
        scanf("%s",ch);
    }

    if(ch[0]=='1')
    {
        system("cls");
        book_publisher();
        book_writer();
        book_stock();
        printf("                               返回上一页请输入Y\n\n");
        printf("                               请输入：");
        scanf("%s",c);
        while(c[1]!='\0'||c[0]!='Y')
        {
             printf("\n                               输入有误，请重新输入！\n\n");
             printf("                               返回上一页请输入Y\n\n");
             printf("                               请输入：");
             scanf("%s",c);
        }
        if(c[0]=='Y')
        {
        system("cls");
        Sta_surface();
        }

   }
   else
   {
       system("cls");
       meun();
   }

}
void book_publisher()
{
    int i=0,j,k,count=0,n;
    char s[10000][50];
    struct book *p;
    p=head;//指针指向头节点
    printf("\n\n                 〓〓〓〓〓〓〓〓〓〓出版社统计〓〓〓〓〓〓〓〓〓〓\n\n");
    while(p!=NULL)
    {
         strcpy(s[i],p->publisher);
         p=p->next;
         i++;
    }
    for(j=0;j<i-1;j++)
    {
         for(k=j+1;k<i;k++)
         {
              if(strcmp(s[j],s[k])==0)
              {
                   n=0;
                   break;
               }
               if(strcmp(s[j],s[k])!=0)
               {
                        n=1;
               }
         }
         if(n==1)
         {
              count++;
              printf("       √%-20s",s[j]);
              if(count%3==0)
              {
                  printf("\n\n");
              }
          }
    }
            printf("\n\n         +                   √馆内书籍出版社共 %d 个\n\n",count);
}

void book_writer()
{
        char a[10000][50];
        struct book *p;
        p=head;//指针指向头节点
        int count=0,i=0,n=0,j,k;
        printf("\n\n                  〓〓〓〓〓〓〓〓〓作者统计〓〓〓〓〓〓〓〓〓\n\n");
        while(p!=NULL)
           {
               strcpy(a[i],p->writer);
               p=p->next;
               i++;
           }
            for(j=0;j<i-1;j++)
            {
                for(k=j+1;k<i;k++)
                {
                    if(strcmp(a[j],a[k])==0)
                    {
                        n=0;
                        break;
                    }
                    if(strcmp(a[j],a[k])!=0)
                    {
                        n=1;
                    }
                }
                if(n==1)
                {
                  count++;
                  if(count%3==1)
                    printf("                   ");
                    printf("√%-10s    ",a[j]);
                   if(count%3==0)
                   {
                     printf("\n\n");
                   }
                }
            }
            printf("\n\n                         +馆内共有 %d 位作者的书籍+\n\n",count);
}
void book_stock()
{
            struct book *p;
            int b,flag=1,i=0,j=0;
            p=head;
            printf("\n\n                     〓〓〓〓〓〓〓〓〓〓库存统计〓〓〓〓〓〓〓〓〓〓");
           printf("\n\n                  ———————————现馆内有库存图书————————\n\n");
           while(p!=NULL)
           {
               if(p->stock!=0)
               {
                   if(i%2==0)
                    printf("                  ");
                   printf("√%-18s  %d 本   ",p->name,p->stock);
                   if(i%2==1)
                    printf("\n\n");
                   b=b+p->stock;
                   i++;
               }
               p=p->next;
           }
           printf("\n\n                  ————————————————————————————\n\n");
           printf("\n                  ——————————-现已被借光图书——————————\n\n");
           p=head;
           while(p!=NULL)
           {
               if(p->stock==0)
               {
                   if(j%2==1)
                    printf("                      ");
                   flag=0;
                   printf("                      √%-18s  %d 本  ",p->name,p->stock);
                   if(j%2==0)
                    printf("\n\n");
               }
               p=p->next;
           }
           if(flag==1)
            printf("\n                                    无\n\n");
            printf("                   ———————————————————————————\n\n");
           printf("                               +现图书馆总库存量： %d 本+\n\n",b);
}
void Del_message(int n)
{
    struct book *p,*q;
    int i;
    char ch[10];
    p=head;
    for(i=1;i<n;i++)
    {
        q=p;
        p=p->next;
    }
        if(head==p)
        {
            head=head->next;
        }
        else
        {
            q->next=p->next;
        }
    free(p);
    write_message();
    printf("\n                               ◆成功删除！\n");
    printf("\n                               是否继续删除图书？继续请输入 Y\n");
    printf("\n                                  返回上一页面请按 F\n\n");
    printf("                                  请输入你的选择：");
    scanf("%s",ch);
            while(ch[1]!='\0')
        {
            printf("\n\n                                  输入有误，请重新输入");
            scanf("%s",ch);
        }
        while(ch[0]!='Y'&&ch[0]!='F')
        {
            printf("\n                                  输入有误，请重新输入");
            scanf("%s",ch);
        }
    switch(ch[0])
    {
        case'Y':system("cls");
                Delect_book();
                break;
        case'F':system("cls");
                Del_surface();
                break;
        default:system("cls");
                meun();
    }


}

void Del_surface()
{
    char ch[10];
    int a=1000;
    printf("\n\n\n                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +                                      〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n");
    printf("                                                                +\n");
    printf("                                 +             +                     \n");
    printf("                      +                                 +\n");
    printf("                           ◆◆◆◆◆◆◆◆◆◆◆◆◆\n");
    printf("    +                           +                          +             +\n");
    printf("                            1.删除图书 2.返回主菜单\n");
    printf("                     +                           +                          +             +\n");
    printf("                           ◆◆◆◆◆◆◆◆◆◆◆◆◆\n");
    printf("      +                           +                          +             +\n");
    printf("                           请输入你要进行的操作序号：");
    scanf("%s",ch);
    printf("                              +             +                 \n");
    printf("                                                               +\n");
    printf("                +                                     +\n");
    while(ch[1]!='\0')
    {
        printf("\n                            输入有误，请重新输入！      +\n");
        printf("\n                     +      请输入你要进行的操作序号：");
        scanf("%s",ch);
    }
    while(ch[0]!='1'&&ch[0]!='2')
    {
        printf("\n                           输入有误，请重新输入！      +\n");
        printf("\n         +           +      请输入你要进行的操作序号：");
        scanf("%s",ch);
    }
    if(ch[0]=='1')
    {
        Sleep(a);
        system("cls");
        Delect_book();
    }
    else
    {
        Sleep(a);
        system("cls");
        meun();
    }
}
void Delect_book()
{
    struct book *p,*q;
    char s[10],ch[10],choice,c[10];
    int flag=0,k=0,i=0,a=1000,t=0,len;
    p=head;
    if(head==NULL)
        {
                    flag=1;
                    printf("\n                           该书库为空**\n");
                    printf("\n                           |请等待系统自动跳转回主菜单\n");
                    Sleep(a);
                    system("cls");
                    meun();
         }
     else
    {
    printf("   +                      +                        +            +\n");
    printf("        +                        +             +                     \n");
    printf("                      +                                 +\n");
    printf("\n     +          +            请输入图书的ISBN号:");
    scanf("%s",s);
    len=strlen(s);
    while(len!=6||s[1]!='-'||s[0]<'A'||s[0]>'V')
    {
        printf("\n                             ◢◣       +               +      +\n");
        printf("     +                     ◢warn◣    编号形式有误，请按照规定格式输入！            +\n");
        printf("                         ◢▲▲▲▲◣\n");
        printf("                  +         +           +                +\n");
        printf("                              ▲重新输入请输入Y，返回上一页请输入N    +   +\n\n");
        printf("  +               +    请选择：");
        scanf("%s",c);
        while(c[1]!='\0')
       {
              printf("                  +         +           +                +              +\n");
              printf("        +            输入有误，请重新输入     + \n");
              printf("                            +         +           +          +      +\n");
              printf("   +              +           ▲重新输入请输入Y，返回上一页请输入N   +         +\n");
              printf("\n                     请选择:");
              scanf("%s",c);
       }
       while(c[0]!='Y'&&c[0]!='N')
       {
        printf("\n           +                 ◢◣       +               +      +\n");
        printf("     +                     ◢warn◣    输入有误，请重新输入      +      +\n");
        printf("                         ◢▲▲▲▲◣          +            +\n");
        printf("                  +         +           +           +     +\n");
        printf("                              ▲重新输入请输入Y，返回上一页请输入N    +           +         +     +\n\n");
        printf("  +                    请选择:");
        scanf("%s",c);
       }
        if(c[0]=='Y')
        {
                system("cls");
                printf("   +                      +                        +            +\n");
                printf("        +                        +             +                     \n");
                printf("                      +                                 +\n");
                printf("\n     +          +            请输入图书的ISBN号:");
                scanf("%s",s);
                len=strlen(s);
        }
        else
        {
              t=1;
              system("cls");
              Del_surface();
              break;
        }
    }
      if(t==0)
       {
               while(p!=NULL)
               {
                   i++;
                 if(strcmp(p->number,s)==0)
                  {
                      flag=1;
                      printf("\n                                     ↓找到了！\n\n");
                      printf("                           ■■■■■■■■■■■■■■■■■■■\n\n");
                      printf("                               ISBN码：");
                      printf("%s\n\n",p->number);
                      printf("                               书名：");
                      printf("%s\n\n",p->name);
                      printf("                               作者：");
                      printf("%s\n\n",p->writer);
                      printf("                               出版社：");
                      printf("%s\n\n",p->publisher);
                      printf("                               出版日期：");
                      printf("%s\n\n",p->date);
                      printf("                               价格：");
                      printf("%.2f\n\n",p->price);
                      printf("                               库存：");
                      printf("%d\n\n",p->stock);
                      printf("                           ■■■■■■■■■■■■■■■■■■■\n\n");
                      printf("                            ▼▼▼▼▼▼▼温馨提示▼▼▼▼▼▼▼\n\n");
                      printf("                                      确认删除请按Y\n\n");
                      printf("                             取消请按F,系统将自动跳转回上一页面~\n\n");
                      printf("                            ▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲\n\n");
                      printf("                                 请输入你的选择：");
                      scanf("%s",ch);
                      while(ch[1]!='\0')
                      {
                          printf("\n                             ◢◣\n");
                          printf("                           ◢warn◣    输入有误，请重新输入\n");
                          printf("                         ◢▲▲▲▲◣\n");
                          printf("\n                               请输入你的选择：");
                          scanf("%s",ch);
                      }
                      while(ch[0]!='Y'&&ch[0]!='F')
                      {
                          printf("\n                             ◢◣\n");
                          printf("                           ◢warn◣    输入有误，请重新输入\n");
                          printf("                         ◢▲▲▲▲◣\n");
                          printf("\n                               请输入你的选择：");
                          scanf("%s",ch);
                      }
                      if(ch[0]=='Y')
                      {
                              Del_message(i);

                      }
                      else
                      {
                              Sleep(a);
                              system("cls");
                              Del_surface();
                      }
                      break;//
                    }
                  p=p->next;
                }
                if(flag==0)
                {
                 printf("\n                    查无此书,请查看ISBN码是否准确\n\n");
                 printf("                          请等待页面自动跳转~");
                 Sleep(a);
                 system("cls");
                 Delect_book();
                }
         }
    }
}
void Search_surface()
{
    char s[10];
    int k=1,a=1000;
    printf("                                 +       +      +                    + \n");
    printf("          +            +                                 +                   + \n");
    printf("                                  +            +             +            +\n");
    printf("                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +           +                          〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n");
    printf("                          +                                     +\n");
    printf("                                 +             +                     \n");
    printf("                      +                                 +\n");
    printf("\n              +            ◆◆◆◆◆◆查找图书◆◆◆◆◆◆◆\n\n");
    printf("                            1.按ISBN码查找     2.按书名查找     +\n");
    printf("             +            +                                 +                   + \n");
    printf("        +          +        3.按作者查找    +  4.按出版社查找     +\n");
    printf("                                 +       +      +                    +           +\n");
    printf("      +                     5.关键字查找       6.按类别查找  +       +      +\n");
    printf("                                 +       +      +                    + \n");
    printf("                  +                 7.返回主菜单\n");
    printf("                                 +             +                     \n");
    printf("       +                   ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
    printf("              +            请选择操作编码：");
    scanf("%s",s);
    if(s[1]!='\0')
    {
        printf("\n               +输入有误，请重新输入+\n");
        printf("\n               +请等待页面更新...+\n");
        Sleep(a);
        system("cls");
        Search_surface();
    }
    switch(s[0])
    {
            case'1':Search_book(s[0]);break;
            case'2':Search_book(s[0]);break;
            case'3':Search_book(s[0]);break;
            case'4':Search_book(s[0]);break;
            case'5':Search_book(s[0]);break;
            case'6':Search_book(s[0]);break;
            case'7':system("cls");
                    meun();
                    break;
            default:printf("\n                +输入有误，请输入对应编号+\n");
                    system("pause");
                    system("cls");
                    Search_surface();
     }
}

void Search_book(char ch)//未完
{
    struct book *p;
    p=head;
    char number[10],w[10],a[10],name[40],writer[20],publisher[50],keyword[40],m[10],n[10],r[10],b[10],s[10],kname[40];
    int len[8],len1[8],k=0,len2,j=0,flag=0,judge=0,len3,i,c=0;
    switch(ch)//出问题！
    {
        case'1':system("cls");
                printf("\n\n\n\n\n\n\n                请输入你要查找的图书ISBN码:");
                scanf("%s",number);
                len[0]=strlen(number);
                len1[0]=strlen(p->number);
                if(len[0]!=len1[0])
                {
                    printf("\n                编号输入有误，请按照格式要求输入！\n");
                    system("pause");
                    system("cls");
                    Search_book(ch);
                }
                if(head==NULL)
                {
                    printf("\n                书库为空！\n");
                    printf("\n                系统将返回主菜单\n");
                    system("pause");
                    system("cls");
                }
                else
                {
                    while(p!=NULL)
                    {
                        if(strcmp(p->number,number)==0&&len[0]==len1[0])
                        {
                            k=1;
                            printf("\n                        +找到该书了+\n\n");
                            printf("                  ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                            printf("                     ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                     书名：");
                            printf("%s\n",p->name);
                            printf("\n                     作者：");
                            printf("%s\n",p->writer);
                            printf("\n                     出版社：");
                            printf("%s\n",p->publisher);
                            printf("\n                     出版日期：");
                            printf("%s\n",p->date);
                            printf("\n                     价格：");
                            printf("%.2f\n",p->price);
                            printf("\n                     库存：");
                            printf("%d 本\n",p->stock);
                            printf("\n                  ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                        }
                        p=p->next;
                    }
                    if(k==0)
                    {
                            printf("\n                     查无此书~\n");
                    }
                           printf("\n                     继续按ISBN码查找图书请输入Y\n");
                           printf("\n                         返回上一页面请按N\n");
                           printf("\n                         请输入：");
                            scanf("%s",a);
                            while(a[1]!='\0')
                            {
                                printf("\n                     输入错误，请重新输入\n");
                                printf("\n                         请输入：");
                                scanf("%s",a);
                            }
                            while(a[0]!='Y'&&a[0]!='N')
                            {
                                printf("\n                     输入错误，请重新输入\n");
                                printf("\n                         请输入：");
                                scanf("%s",a);
                            }
                            if(a[0]=='Y')
                            {
                                system("cls");
                                Search_book(ch);
                            }
                            else
                            {
                                system("cls");
                                Search_surface();
                            }

                    }
                break;
        case'2':k=0;
                system("cls");
                printf("\n\n\n\n\n\n                      请输入书名:");
                scanf("%s",name);
                len[1]=strlen(name);
                if(head==NULL)
                {
                    printf("\n                     书库为空！\n");
                    printf("\n                     系统将返回主菜单\n");
                    system("pause");
                    system("cls");
                }
                else
                {
                    while(p!=NULL)
                    {
                        len1[1]=strlen(p->name);
                        if(strcmp(p->name,name)==0&&len[1]==len1[1])
                        {
                            k=1;
                            printf("\n                     ◆◆◆◆◆◆◆书名查找◆◆◆◆◆◆\n\n");
                            printf("                         ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                         书名：");
                            printf("%s\n\n",p->name);
                            printf("                         作者：");
                            printf("%s\n\n",p->writer);
                            printf("                         出版社：");
                            printf("%s\n\n",p->publisher);
                            printf("                         出版日期：");
                            printf("%s\n\n",p->date);
                            printf("                         价格：");
                            printf("%.2f\n\n",p->price);
                            printf("                         库存：");
                            printf("%d 本\n\n",p->stock);
                            printf("                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                        }
                        p=p->next;
                    }
                    if(k==0)
                    {
                            printf("\n                     查无此书~\n");
                    }
                       printf("\n                      继续按书名查找图书请输入Y\n");
                       printf("\n                        返回上一页面请按N\n");
                       printf("\n                        请输入：");
                       scanf("%s",m);
                        while(m[1]!='\0')
                            {
                                printf("\n                     输入错误，请重新输入！\n");
                                printf("\n                        请输入：");
                                scanf("%s",m);
                            }
                            while(m[0]!='Y'&&m[0]!='N')
                            {
                                printf("\n                     输入错误，请重新输入\n");
                                printf("\n                        请输入：");
                                scanf("%s",m);
                            }
                            if(m[0]=='Y')
                            {
                                system("cls");
                                Search_book(ch);
                            }
                            else
                            {
                                system("cls");
                                Search_surface();
                            }
                    }
                break;
        case'3':k=0;
                system("cls");
                printf("\n\n\n\n\n\n                     请输入作者:");
                scanf("%s",writer);
                len[2]=strlen(writer);
                if(head==NULL)
                {
                    printf("\n                     书库为空！\n");
                    printf("\n                     系统将返回主菜单\n");
                    system("pause");
                    system("cls");
                }
                else
                {
                    while(p!=NULL)
                    {
                        len1[2]=strlen(p->writer);
                        if(strcmp(p->writer,writer)==0&&len[2]==len1[2])
                        {
                            k=1;
                            printf("\n\n                     ◆◆◆◆◆◆作者查找◆◆◆◆◆◆◆\n\n");
                            printf("                       ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                       书名：");
                            printf("%s\n\n",p->name);
                            printf("                       作者：");
                            printf("%s\n\n",p->writer);
                            printf("                       出版社：");
                            printf("%s\n\n",p->publisher);
                            printf("                       出版日期：");
                            printf("%s\n\n",p->date);
                            printf("                       价格：");
                            printf("%.2f\n\n",p->price);
                            printf("                       库存：");
                            printf("%d 本\n",p->stock);
                            printf("\n                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                        }
                        p=p->next;
                    }
                    if(k==0)
                    {
                        printf("\n                     没有该作者的相关书籍~\n");
                    }
                       printf("\n                     继续按作者查找图书请输入Y\n");
                       printf("\n                        返回上一页面请按N\n");
                       printf("\n                        请输入：");
                    scanf("%s",n);
                    while(n[1]!='\0')
                    {
                          printf("\n                     输入错误，请重新输入！\n");
                          printf("\n                        请输入:");
                          scanf("%s",n);
                    }
                     while(n[0]!='Y'&&n[0]!='N')
                     {
                           printf("\n                     输入错误，请重新输入\n");
                           printf("\n                        请输入：");
                           scanf("%s",n);
                     }
                    if(n[0]=='Y')
                    {
                          system("cls");
                          Search_book(ch);
                    }
                    else
                    {
                           system("cls");
                           Search_surface();
                    }
              }
              break;
        case'4':k=0;
                system("cls");
                printf("\n\n\n\n\n\n                     请输入出版社:");
                scanf("%s",publisher);
                len[3]=strlen(publisher);
                if(head==NULL)
                {
                    printf("\n                     书库为空！\n");
                    printf("\n                     系统将返回主菜单\n");
                    system("pause");
                    system("cls");
                }
                else
                {
                    while(p!=NULL)
                    {
                        len1[3]=strlen(p->publisher);
                        if(strcmp(p->publisher,publisher)==0&&len[3]==len1[3])
                        {
                            k=1;
                            printf(" \n\n                     ◆◆◆◆◆按出版社查找◆◆◆◆◆\n\n");
                            printf("                        ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                        书名：");
                            printf("%s\n\n",p->name);
                            printf("                        作者：");
                            printf("%s\n\n",p->writer);
                            printf("                        出版社：");
                            printf("%s\n\n",p->publisher);
                            printf("                        出版日期：");
                            printf("%s\n\n",p->date);
                            printf("                        价格：");
                            printf("%.2f\n\n",p->price);
                            printf("                        库存：");
                            printf("%d 本\n",p->stock);
                            printf("\n                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                        }
                        p=p->next;
                    }
                    if(k==0)
                    {
                        printf("\n                     没有该出版社的相关书籍~\n");
                    }

                    printf("\n                      继续按出版社查找图书请输入Y\n");
                    printf("\n                        返回上一页面请按N\n");
                    printf("\n                         请输入：");
                    scanf("%s",w);
                    while(w[1]!='\0')
                    {
                          printf("\n                       输入错误，请重新输入\n");
                          printf("\n                        请输入：");
                          scanf("%s",w);
                    }
                    while(w[0]!='Y'&&w[0]!='N')
                    {
                          printf("\n                       输入错误，请重新输入\n");
                          printf("\n                        请输入：");
                          scanf("%s",w);
                    }
                    if(w[0]=='Y')
                    {
                          system("cls");
                          Search_book(ch);
                    }
                    else
                    {
                           system("cls");
                           Search_surface();
                    }
              }
              break;
        case'5':k=0;
                system("cls");
                printf("\n\n\n\n");
                printf("                     请输入关键字：");
                scanf("%s",keyword);
                len3=strlen(keyword);
                while(p!=NULL)
                {
                    j=0;
                    judge=0;//用来判断关键字是否与书名匹配成功
                    strcpy(kname,p->name);
                    len2=strlen(kname);
                    for(i=0;i<len2;i++)
                    {
                        if(keyword[j]==kname[i])
                        {
                            j++;
                        }
                        else
                            j=0;
                        if(j==len3)
                        {
                            judge=1;
                            break;
                        }

                    }
                    if(judge==1)
                    {
                            c=1;//用于判断是否有相关书籍
                            printf("\n                     ◆◆◆◆◆关键字查找◆◆◆◆◆\n\n");
                            printf("                        ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                        书名：");
                            printf("%s\n\n",p->name);
                            printf("                        作者：");
                            printf("%s\n\n",p->writer);
                            printf("                        出版社：");
                            printf("%s\n\n",p->publisher);
                            printf("                        出版日期：");
                            printf("%s\n\n",p->date);
                            printf("                        价格：");
                            printf("%.2f\n\n",p->price);
                            printf("                        库存：");
                            printf("%d 本\n\n",p->stock);
                            printf("                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n");

                    }
                    p=p->next;
                }
                if(c==0)//若c==0，则没有
                {
                    printf("\n                        搜索不到相关书籍\n");
                }
                printf("\n                      继续按关键字查找图书输入Y\n");
                printf("\n                        返回上一页面请按N\n");
                printf("\n                        请输入你的选择：");
                scanf("%s",b);
                while(b[0]!='Y'&&b[0]!='N'||b[1]!='\0')
                {
                    printf("\n                     输入错误，请重新输入！\n");
                    printf("\n                        请输入你的选择：");
                    scanf("%s",b);
                }
                if(b[0]=='Y')
                {
                    system("cls");
                    Search_book(ch);
                }
                else
                {
                     system("cls");
                    Search_surface();
                }
                break;
        case'6':k=0;
                system("cls");
                printf("\n\n\n                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                printf("                     A　马克思主义、列宁主义、毛泽东思想     B　哲学\n\n");
                printf("                     C　社会科学总论                         D　政治、法律\n\n");
                printf("                     E　军事                                 F　经济\n\n");
                printf("                     I　文学                                 J　艺术\n\n");
                printf("                     K　历史、地理                           N　自然科学总论\n\n");
                printf("                     O　数理科学和化学                       P　天文学、地理科学\n\n");
                printf("                     Q　生物科学                             R　医学、卫生\n\n");
                printf("                     S　农业科学                             T　工业技术\n\n");
                printf("                     U　交通运输                             V  航空、航天\n\n");
                printf("                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n\n");
                printf("\n                        根据你想查询的图书类别，输入对应编号：");
                scanf("%s",r);
                while(r[1]!='\0'||r[0]<'A'||r[0]>'V')
                {
                    printf("\n                         输入有误,请重新输入！");
                    scanf("%s",r);
                }
                if(r[0]>='A'&&r[0]<='V')
                {
                    while(p!=NULL)
                    {
                    strcpy(s,p->number);
                    if(r[0]==s[0])
                    {
                            k=1;
                            printf(" \n\n                     ◆◆◆◆◆◆◆◆类别查找◆◆◆◆◆◆◆\n\n");
                            printf("                          ISBN码:");
                            printf("%s\n\n",p->number);
                            printf("                          书名：");
                            printf("%s\n\n",p->name);
                            printf("                          作者：");
                            printf("%s\n\n",p->writer);
                            printf("                          出版社：");
                            printf("%s\n\n",p->publisher);
                            printf("                          出版日期：");
                            printf("%s\n\n",p->date);
                            printf("                          价格：");
                            printf("%.2f 元\n\n",p->price);
                            printf("                          库存：");
                            printf("%d 本\n",p->stock);
                            printf("\n                     ◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆◆\n");
                    }
                    p=p->next;
                    }
                }
                  if(k==0)
                  {
                        printf("\n                          暂无该类别的相关书籍~\n");
                  }
                    printf("\n                          继续按类别查找图书请输入Y\n");
                    printf("\n                           返回上一页面请输入N\n");
                    printf("\n                             请输入你的选择：");
                    scanf("%s",r);
                    while(r[1]!='\0')
                    {
                          printf("\n                          输入错误，请重新输入！\n");
                          printf("\n                             请输入你的选择：");
                          scanf("%s",r);
                    }
                    while(r[0]!='Y'&&r[0]!='N')
                    {
                          printf("\n                          输入错误，请重新输入！\n");
                          printf("\n                             请输入你的选择：");
                          scanf("%s",r);
                    }
                    if(r[0]=='Y')
                    {
                          system("cls");
                          Search_book(ch);
                    }
                    else
                    {
                           system("cls");
                           Search_surface();
                    }
        break;
        default:printf("                        输入有误！\n");

    }

}
void Input_surface()
{
    char ch[10];
    printf("\n\n\n                   〓〓〓〓      〓〓〓〓〓〓〓〓      〓〓〓〓       +\n");
    printf("              +                  〓        +         +              \n");
    printf("                                 + 图书管理系统            +       \n");
    printf("        +           +                          〓            \n");
    printf("                            +    〓〓〓〓〓〓〓〓    +        +    \n");
    printf("                          +                                     +\n");
    printf("                                 +             +                     \n");
    printf("                      +                                 +\n");
    printf("                     ______________Please choose______________  \n");
    printf("                      +                                 +\n");
    printf("                       ┍____________┒      ┍____________┒\n\n");
    printf("                         1.新增图书            2.返回主菜单\n");
    printf("                       ┕            ┙      ┕            ┙\n\n");
    printf("     +                             +  请输入你的选择：");
    scanf("%s",ch);
    while(ch[1]!='\0'||ch[0]<'1'||ch[0]>'2')
    {

        printf("                               输入有误，请重新输入！\n\n");
        printf("                                       请输入你的选择：");
        scanf("%s",ch);
    }
    if(ch[0]=='1')
    {
        system("cls");
        Input_newbook();
    }
    else
    {
        system("cls");
        meun();
    }

}
void Input_newbook()//新增图书//再次输入时出问题了！！！
{
    struct book *newbook,*p,*q;
    FILE *fp;
    fp=fopen("books.txt","a");
    p=head;
    int stock,a=1000,flag=0,t,len;
    char name[50], number[10];
    char m[10],k[10];
    char writer[20],date[10];
    char publisher[100];
    double price;
    printf("\n\n\n                             图书编号采用如A-0000形式\n");
                   printf("                       ________________________________________________________\n\n");
                   printf("                        A　马克思主义、列宁主义、毛泽东思想义   B　哲学\n\n");
                   printf("                        C　社会科学总论                         D　政治、法律\n\n");
                   printf("                        E　军事                                 F　经济\n\n");
                   printf("                        I　文学                                 J　艺术\n\n");
                   printf("                        K　历史、地理                           N　自然科学总论\n\n");
                   printf("                        O　数理科学和化学                       P　天文学、地理科学\n\n");
                   printf("                        Q　生物科学                             R　医学、卫生\n\n");
                   printf("                        S　农业科学                             T　工业技术\n\n");
                   printf("                        U　交通运输                             V  航空、航天\n\n");
                   printf("                       ________________________________________________________\n\n");
    printf("                               请输入图书的ISNB号:");
    scanf("%s",number);
    len=strlen(number);
    while(len!=6||number[1]!='-'||number[0]<'A'||number[0]>'V')
    {
        printf("\n                                  输入编号形式有误，请按照规定形式输入\n");
        printf("\n                               请输入图书的ISBN号：");
        scanf("%s",number);
        len=strlen(number);
    }
    while(p!=NULL)
    {
       if(strcmp(p->number,number)==0)//当图书编号已存在书，增加该图书的库存。
       {
        flag=1;
        printf("\n\n                                  √该图书已有库存！\n");
        printf("\n                                  ↓信息如下！\n");
        printf("                       __________________________________________\n\n");
        printf("\n                                  ISBN码：");
        printf("%s\n\n",p->number);
        printf("                                  书名：");
        printf("%s\n\n",p->name);
        printf("                                  作者：");
        printf("%s\n\n",p->writer);
        printf("                                  出版社：");
        printf("%s\n\n",p->publisher);
        printf("                                  出版日期：");
        printf("%s\n\n",p->date);
        printf("                                  价格：");
        printf("%.2f\n\n",p->price);
        printf("                                  库存：");
        printf("%d 本\n\n",p->stock);
        printf("                       __________________________________________\n\n");
        printf("                                  请输入新增图书数量:");
        scanf("%d",&t);
        printf("\n");
        p->stock=p->stock+t;
        write_message();//将新增图书信息写进文件中；
        getchar();
     //   system("pause");//
        printf("\n                                  ▲图书已入库！\n");
        printf("\n                                  继续新增图书请输入Y\n");
        printf("\n                                   返回上一页请输入N\n");
        printf("\n                                    请选择：");
        scanf("%s",m);
        while(m[1]!='\0')
        {
            printf("\n\n                                  输入有误，请重新输入");
            scanf("%s",m);
        }
        while(m[0]!='Y'&&m[0]!='N')
        {
            printf("\n                                  输入有误，请重新输入");
            scanf("%s",m);
        }
        if(m[0]=='Y')
        {

            system("cls");
            Input_newbook();
            break;
        }
        else
        {
            system("cls");
            Input_surface();
            break;
        }

       }
       p=p->next;
    }
    if(flag==0)
    {
    printf("                +                   +");
    printf("         +            +       +            +");
    printf("\n                                  请输入书名:");
    scanf("%s",name);
    printf("\n                                  请输入作者:");
    scanf("%s",writer);
    printf("\n                                  请输入出版社:");
    scanf("%s",publisher);
    printf("\n                                  请输入出版日期:");
    scanf("%s",date);
    printf("\n                                  请输入图书价格:");
    scanf("\n%lf",&price);
    printf("\n                                  请输入图书库存:");
    scanf("%d",&stock);
        q=(struct book *)malloc(sizeof(struct book));
           strcpy(q->name,name);
           strcpy(q->number,number);
           strcpy(q->writer,writer);
           strcpy(q->publisher,publisher);
           strcpy(q->date,date);
           q->price=price;
           q->stock=stock;
           p=head;//不加上去就会出错的！！！
         while(p->next!=NULL)
        {
           p=p->next;
       }
           p->next=q;
           p=q;//
           p->next=NULL;//尾插法
        write_message();////出问题了
        printf("\n\n                                  ▲图书已成功录入！\n");
        getchar();
        printf("\n                                  继续按录入图书请输入Y\n");
        printf("\n                                  返回上一页面请输入N\n");
        printf("\n                                  请选择：");
        scanf("%s",k);
        while(k[1]!='\0')
        {
            printf("\n                                  输入有误，请重新输入");
            printf("\n                                  请选择：");
            scanf("%s",k);
        }
        while(k[0]!='Y'&&k[0]!='N')
        {
            printf("\n                                  输入有误，请重新输入");
            printf("\n                                  请选择：");
            scanf("%s",k);
        }
        if(k[0]=='Y')
        {

            system("cls");
            Input_newbook();
        }
        else
        {
            system("cls");
            Input_surface();
        }
    }
}

