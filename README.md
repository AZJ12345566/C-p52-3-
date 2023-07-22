# C-p52-3-
C语言学习笔记 p52 字符函数&内存函数使用和剖析(3)
//字符函数和内存函数的区别是：字符函数的操作对象是字符串，内存函数的操作对象是
#include<stdio.h>
#include<string.h>
#include<assert.h>
int main()
{
    int arr1[]={1,2,3,4,5};
    int arr2[5]={0};
    strcpy(arr2,arr1);
    return 0;
}//输出1，这里的1是小端存储的第一个字节，打印第二个字节的时候，发现第二个字节是0，停止打印
//这就是字符函数的局限
//内存函数：memcpy,memmove,memcmp,memset
//内存函数啥类型都能拷贝，类型参数都是void*


//memcpy库函数模版参数：
//void* memcpy(void* dest,const void* src,size_t num);
//实现my_memcpy
void* my_memcpy(void* dest,const void* src,size_t num)
{
      void* ret=dest;
      assert(dest!=NULL);
      assert(src!=NULL);
      while(num--)
      {
          *(char*)dest=*(char*)src;
          ++(char*)dest;
          ++(cahr*)src;
      }
      return ret;
}
int main()
{
    int arr1[]={1,2,3,4,5};
    int arr2[5]={0};
    my_memcpy(arr1,arr2,sizeof(arr1));
    return 0;
}

int main()
{
    int arr[]={1,2,3,4,5,6,7,8,9,10};
    my_memcpy(arr+2,arr,20);
    for(i=0;i<10;i++)
    {
        printf("%d\n",arr[i]);
    }
    return 0;
}//这里想让1，2，3，4，5拷贝到3，4，5，6，7中memcpy在这里就行不通了，涉及重叠拷贝就用memmove

//memmove的函数参数和memcpy是一模一样的

void* my_memmove(void* dest,void* src,size_t num)
{
}
//dest落在src左边，从前向后拷贝。dest落在src中间，从后向前拷贝，dest落在src左边就随便怎么拷
int main()
{
    int arr[]={1,2,3,4,5,6,7,8,9,10};
    my_memmove(arr+2,arr,20);
    for(i=0;i<10;i++)
    {
        printf("%d\n",arr[i]);
    }
    return 0;
}//C语言规定，memcpy处理不重叠的想象就可以了，memmove就可以处理重叠的现象

int main()
{
    
    return 0;
}
