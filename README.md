#include <stdio.h>
#include <stdlib.h>

#define MAXSIZE 5
struct List
{
    int element;
};
int createlist()
{
    struct List L[MAXSIZE],*Ptrl;
    Ptrl=L;
    int i=1;
    for(i;i<=MAXSIZE-1;++i)
    {
        printf("请输入线性表的第%d个元素",i);
        scanf("%d",&Ptrl->element);
    }
}
int insert(struct List L[],int i,struct List p)
{
    if(i<1||i>MAXSIZE)
    {
        return 0;
    }
    else
    {
    struct List *q,*k;
    q=&(L[i-1]);
    for(k=L+MAXSIZE-1;k>=q;--k)
        *(k+1)=*k;
        q->element=p.element;
        return 1;
    }
}
int delete1(struct List L[],int i)
{
    if((i<1)||(i>MAXSIZE))
        return 0;
    struct List *p,*q;
    p=&(L[i]);
    q=L+MAXSIZE-1;
    for(p+1;p<=q;++p)
        (p-1)->element=p->element;
    return 1;
}
int main()
{
    struct List L[MAXSIZE],*Ptrl;
    Ptrl=L;
    int i=1;
    for(i;i<=MAXSIZE-1;++i)
    {
        printf("请输入线性表的第%d个元素",i);
        scanf("%d",&Ptrl->element);
        Ptrl++;
    }
    for(i=1;i<=MAXSIZE-1;++i)
    {
        printf("%d ",L[i-1]);
    }
    int j,k,l;
    struct List input;
    struct List ele;
    printf("\n");
    printf("请输入要插入的元素");
    scanf("%d",&input.element);
    printf("请输入要插入的位置");
    scanf("%d",&j);
    k=insert(L,j,input);
    if(k=0)
    {
        printf("插入失败");
    }
    else
    {
        printf("插入成功\n");
        for(i=1;i<=MAXSIZE;++i)
          printf("%d ",L[i-1]);
    }
    printf("\n");
    printf("请输入要删除的元素的位置");
    scanf("%d",&l);
    ele.element=L[l-1].element;
    k=delete1(L,l);
    if(!k)
    {
        printf("删除失败");
    }
    else
    {
        printf("删除成功\n");
        for(i=1;i<MAXSIZE;++i)
            printf("%d ",L[i-1]);
        printf("被删除的元素是%d",ele.element);
    }
}
