# osAssignment
#include<stdio.h>
struct node;
typedef struct node *ptrtonode;
typedef ptrtonode memory;
typedef struct node nodetype;
int pro_id,pro_size;
memory create();
struct node
{
int  id;
 int start;
int hole;
int  end;
ptrtonode next;
};
memory create()
{
memory mem;
mem=(ptrtonode)malloc(sizeof(nodetype));
mem->next=NULL;
return mem;
}
void insert(memory mem,int s,int e)
{
ptrtonode tmp;
tmp=(ptrtonode)malloc(sizeof(nodetype));
tmp->next=mem->next;
tmp->start=s;
tmp->end=e;
tmp->hole=e-s;
tmp->id=0;
mem->next=tmp;
}
void firstfit(memory mem)
{
int diff;
ptrtonode tmp;
tmp=mem->next;
while(tmp!=NULL)
{
if(tmp->hole>=pro_size&&tmp->id==0)
{
tmp->id=pro_id;
diff=tmp->hole-pro_size;
tmp->hole=0;
tmp->end=tmp->start+pro_size;
if(tmp->next!=NULL&&tmp->next->hole==0)
{
tmp=tmp->next;
tmp->hole+=diff;
tmp->start-=diff;
}
else
{
ptrtonode t;
t=(ptrtonode)malloc(sizeof(nodetype));
t->next=tmp->next;
tmp->next=t;
t->id=0;
t->hole=diff;
t->start=tmp->end;
t->end=t->start+t->hole;
}
break;
}
Else
tmp=tmp->next;
}
}
void best_fit(memory mem)
{
int diff,count=0,c,min;
ptrtonode tmp;
tmp=mem->next;
min=3200;
while(tmp!=NULL)
{
count++;
if(tmp->hole>=pro_size&&tmp->id==0)
if(tmp->hole<min)
{
min=tmp->hole;
c=count;
}
tmp=tmp->next;
}
tmp=mem->next;
count=0;
while(tmp!=NULL)
{
count++;
if(c==count)
{
tmp->id=pro_id;
diff=tmp->hole-pro_size;
tmp->hole=0;
tmp->end=tmp->start+pro_size;
if(tmp->next!=NULL&&tmp->next->hole==0)
{
tmp=tmp->next;
tmp->hole+=diff;
tmp->start-=diff;
}
else
{
prtonode t;
t=(ptrtonode)malloc(sizeof(nodetype));
t->next=tmp->next;
tmp->nex=t;
t->id=0;
t->hole=diff;
t->start=tmp->end;
t->end=t->start+t->hole;
}
Break;
}
tmp=tmp->next;
}
}
void worst_fit(memory mem)
{
int diff,count=0,c,max;
ptrtonode tmp;
tmp=mem->next;
max=-1;
while(tmp!=NULL)
{
count++;
if(tmp->hole>=pro_size&&tmp->id==0)
if(tmp->hole>max)
{
max=tmp->hole;
c=count;
}
tmp=tmp->next;
{
count++;;
if(c==count)
{
tmp->id=pro_id;
diff=tmp->hole-pro_size;
tmp->hole=0;
tmp->end=tmp->start+pro_size;
if(tmp->next!=NULL&&temp->next->hole==0)
{
tmp=tmp->next;
tmp->hole+=diff;
tmp->start-=diff;
}
Else
{
Ptrtonode t;
t=(ptrtonode)malloc(sizeof(nodetype));
t->next=tmp->next;
tmp->next=t;
t->hole=diff;
t->id=0;
t->start=tmp->end;
t->end=t->start+t->hole;
}
Break;
}
tmp=tmp->next;
}
}
void allocate(memory mean)
{
Int opt;
printf(“\nEnter the process ID:”);
scanf(“%d”,&pro_id);
printf(“\n Enter the process size:”);
scanf(“%d”,&pro_size);
printf(“\nMENU”);
printf(“\n1.FIRST FIT”);
printf(“\n2.BEST FIT”);
printf(“\n3.WORST  FIT”);
printf(“\nEnter your option”);
scanf(“%d”,opt);
switch(opt)
{
case 1:
first_fit(mem);
break;
case 2:
best_fit(mem);
break;
}
}
void deallocate(memory mem)
{
prtonode tmp;
int diff;
printf(“\nEnter the process ID:”);
scanf(“%d”,&pro_id);
tmp=mem;
while(tmp->next!=NULL)
{
if(tmp->next->id==pro_id)
{
Ptrtonode
t=tmp->next;
t->id=0;
t->next->start=t->start;
t->next->hole=t->next->end-t->next->start;
tmp->next=t->next;
free(t);
}
Else
{
t->id=0;
t->hole=t->end-t->start;
}
break;
}
tmp=tmp->next;
}
}
void display(memory mem)
{
ptrtonode tmp;
tmp=mem->next;
while(tmp!=NULL)
{
tmp=tmp->next;
}
}
void del(memory mem)
{
ptrtonode tmp,tmp,t;
tmp=mem;
while(tmp!=NULL)
{
t=tmp->next;
free(t);
tmp=t;
}
free(mem);
}
int main()
{
int i,opt,mem_end=8000,mem_start;
memory mem;
mem=create();
insert(mem,0,10000);
for(;;)
{
printf(“\nMENU”);
printf(“\n1.Allocate  memory”);
printf(“\n2.Deallocate Memory”);
printf(“\n3.Display”);
printf(“\n4.Exit”);
printf(“\nEnter your Option”);
scanf(“%d”,&opt);
switch(opt)
{
case 1:
allocate(mem);
break;
case 2:
deallocate(mem);
break;
case 3:
display(mem);
break;
case 4:
del(mem);
exit(0);
}
}
Return 0;
