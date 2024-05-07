# library management
#include <stdio.h>
#include <string.h>
void admin();
void student();
void add();
void view();
void viewissue();
void login();
void signup();
void search();
void lend();
void retur();
struct stu
{
    char a[100];
    int g,p;
}s[100];
struct book
{
    char bn[200],an[100];
    int p,f;
}bk[100];
int t=0,st=0;
int main()
{
    int n;
    printf("--------------------------------------------\n");
    printf("-------- Useless Library Management --------\n");
    printf("--------------------------------------------");
    while(1)
    {
        printf("\n1.Admin\n2.Student\n3.Exit\nEnter a chioce : ");
        scanf("%d",&n);
        if(n==1)
            admin();
        else if(n==2)
            student();
        else
        {
            printf("\n!!!!! ........ Thank You ......... !!!!");
            break;
        }
    }
    return 0;
}
void admin()
{
    int n,i,p;
    printf("Enter Admin Id : ");
    scanf("%d",&i);
    printf("Enter Admin password : ");
    scanf("%d",&p);
    if(i==2023 && p==123)
    {
        while(1)
        {
            printf("\n1.Add\n2.viewissue\n3.save report\n4.Exit\nEnter a chioce : ");
            scanf("%d",&n);
            if(n==1)
                add();
            else if(n==2)
                viewissue();
            else
                break;
        }
    }
    else
        printf("Invalid id Or password ");
}
void student()
{
    int n;
    while(1)
    {
        printf("\n1.Login\n2.SignUp\n3.Exit\nEnter a chioce : ");
        scanf("%d",&n);
        if(n==1)
            login();
        else if(n==2)
            signup();
        else
            break;
    }
}
void signup()
{
    printf("Enter a Student name :");
    scanf("%s",s[st].a);
    printf("Enter a Student age :");
    scanf("%d",&s[st].g);
    printf("Enter a Student password :");
    scanf("%d",&s[st].p);
    printf("Student id is : %d\n",st+200);
    st++;
}
void login()
{
    int n,i,t;
    printf("Enter Student Id : ");
    scanf("%d",&n);
    printf("Enter Student password : ");
    scanf("%d",&t);
    if(s[n-200].p==t)
    {
        while(1)
        {
            printf("\n1.View book\n2.Search book\n3.Lend book\n4.return book\n5.Exit\nEnter a chioce : ");
            scanf("%d",&n);
            if(n==1)
                view();
            else if(n==2)
                search();
            else if(n==3)
                lend();
            else if(n==4)
                retur();
            else
                break;
        }
    }
    else
        printf("Invalid id Or password ");
}
void add()
{
    int n,i;
    printf("\nEnter a no.of book : ");
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        printf("Enter a book name :");
        scanf("%s",bk[t].bn);
        printf("Enter a author name :");
        scanf("%s",bk[t].an);
        printf("Enter a price :");
        scanf("%d",&bk[t].p);
        printf("book id is : %d\n",t+100);
        bk[t].f=1;
        t++;
    }
}
void view()
{
    int i,f=1;
    for(i=0;i<t;i++)
    {
        if(bk[i].f==1)
        {
            printf("book name : %s\nauthor name : %s\nprice : %d\nbook id : %d\n\n",bk[i].bn,bk[i].an,bk[i].p,i+100);
            f=0;
        }
    }
    if(f)
        printf("Not Avelable book \n");
}
void viewissue()
{
    int i,f=1;
    for(i=0;i<t;i++)
    {
        if(bk[i].f==0)
        {
            printf("book name : %s\nauthor name : %s\nprice : %d\nbook id : %d\n\n",bk[i].bn,bk[i].an,bk[i].p,i+100);
            f=0;
        }
    }
    if(f)
        printf("Not Avelable book \n");
}
void lend()
{
    int n;
    printf("Enter a Book Id :");
    scanf("%d",&n);
    if(100<=n && n<(t+100))
    {
        bk[n-100].f=0;
        printf("Lend Successfully ... ");
    }
    else
        printf("Invalid Book id");
}
void retur()
{
    int n;
    printf("Enter a Book Id :");
    scanf("%d",&n);
    if(100<=n && n<(t+100))
    {
        bk[n-100].f=1;
        printf("Return Successfully ... ");
    }
    else
        printf("Invalid Book id");
}
void search()
{
    char a[100];
    int i,f=1;
    printf("Enter a Book name :");
    scanf("%s",a);
    for(i=0;i<t;i++)    
    {
        if(!strcmp(bk[i].bn,a))
        {
            printf("book name : %s\nauthor name : %s\nprice : %d\nbook id : %d\n\n",bk[i].bn,bk[i].an,bk[i].p,i+100);
            f=0;
            break;
        }
    }
    if(f)
        printf("book not avaliable ... ");
}
// void save()
// {
    
// }



