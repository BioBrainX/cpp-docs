---
title: "pair (STL-CLR)"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
H1: pair (STL/CLR)
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: 5
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# pair (STL-CLR)
The template class describes an object that wraps a pair of values.  
  
## Syntax  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### Parameters  
 Value1  
 The type of first wrapped value.  
  
 Value2  
 The type of second wrapped value.  
  
## Members  
  
|Type Definition|Description|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](../VS_visualcpp/pair--first_type--STL-CLR-.md)|The type of the first wrapped value.|  
|[pair::second_type (STL/CLR)](../VS_visualcpp/pair--second_type--STL-CLR-.md)|The type of the second wrapped value.|  
  
|Member Object|Description|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../VS_visualcpp/pair--first--STL-CLR-.md)|The first stored value.|  
|[pair::second (STL/CLR)](../VS_visualcpp/pair--second--STL-CLR-.md)|The second stored value.|  
  
|Member Function|Description|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../VS_visualcpp/pair--pair--STL-CLR-.md)|Constructs a pair object.|  
|[pair::swap (STL/CLR)](../VS_visualcpp/pair--swap--STL-CLR-.md)|Swaps the contents of two pairs.|  
  
|Operator|Description|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../VS_visualcpp/pair--operator=--STL-CLR-.md)|Replaces the stored pair of values.|  
  
## Remarks  
 The object stores a pair of values. You use this template class to combine two values into a single object. Note that `cliext::pair` (described here) stores only managed types; to store a pair of unmanaged types use `std::pair`, declared in `<utility>`.  
  
## Requirements  
 **Header:** <cliext/utility>  
  
 **Namespace:** cliext  
  
## See Also  
 [make_pair (STL/CLR)](../VS_visualcpp/make_pair--STL-CLR-.md)