---
title: "operator&lt;= (list) (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: ["cpp-windows"]
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: ["cliext::list::operator<="]
dev_langs: ["C++"]
helpviewer_keywords: ["operator<= member [STL/CLR]"]
ms.assetid: af677e20-f529-4055-b101-af9728bc090b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
ms.workload: ["cplusplus", "dotnet"]
---
# operator&lt;= (list) (STL/CLR)
List less than or equal comparison.  
  
## Syntax  
  
```  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### Parameters  
 left  
 Left container to compare.  
  
 right  
 Right container to compare.  
  
## Remarks  
 The operator function returns `!(right < left)`. You use it to test whether `left` is not ordered after `right` when the two lists are compared element by element.  
  
## Example  
  
```  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## Requirements  
 **Header:** \<cliext/list>  
  
 **Namespace:** cliext  
  
## See Also  
 [list (STL/CLR)](../dotnet/list-stl-clr.md)   
 [operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operator\< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)   
 [operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)