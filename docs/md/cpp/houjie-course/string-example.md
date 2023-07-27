# string 例子（数据中带有指针）

## big three

## 内存分配

stack 和 heap

## 代码示例

```cpp

// String.h
#ifndef __String__
#define __String__

#include <strings.h>

class String
{
public:
    // 构造函数
    String(const char* m = 0):m_data(m){}
    // 拷贝构造函数
    String(const String& m)
    // 拷贝赋值函数
    String& operator= (const String& m)
    // 析构函数
    ~String()
    // 操作符重载
    ostream& operator<< (ostream& ths, const String& s)
    // 内联函数
    inline char* get_m_data const (){
        return m_data;
    }
private:
    char* m_data;
}

String:String(const String& m){
    if(m){
        return m_data = new String();
    }
    else{
        String* p = new String(m.m_data);
        m_data = p;
    }
}


#endif
```

```cpp
// String-test.cpp

#include <iostream>
#include "String.h"

int main()
{

    return 0;
}
```
