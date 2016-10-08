---
title: "Property Map Macros"
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
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: 12
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
# Property Map Macros
These macros define property maps and entries.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md)|Marks the beginning of the ATL property map.|  
|[PROP_DATA_ENTRY](../Topic/PROP_DATA_ENTRY.md)|Indicates the extent, or dimensions, of an ActiveX control.|  
|[PROP_ENTRY_TYPE](../Topic/PROP_ENTRY_TYPE.md)|Enters a property description, property DISPID, and property page CLSID into the property map.|  
|[PROP_ENTRY_TYPE_EX](../Topic/PROP_ENTRY_TYPE_EX.md)|Enters a property description, property DISPID, property page CLSID, and                             `IDispatch` IID into the property map.|  
|[PROP_PAGE](../Topic/PROP_PAGE.md)|Enters a property page CLSID into the property map.|  
|[END_PROP_MAP](../Topic/END_PROP_MAP.md)|Marks the end of the ATL property map.|  
  
##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP  
 Marks the beginning of the object's property map.  
  
```  
  
BEGIN_PROP_MAP(  
theClass  
)  
  
```  
  
### Parameters  
 `theClass`  
 [in] Specifies the class containing the property map.  
  
### Remarks  
 The property map stores property descriptions, property DISPIDs, property page CLSIDs, and                         `IDispatch` IIDs. Classes                         [IPerPropertyBrowsingImpl](../VS_visualcpp/IPerPropertyBrowsingImpl-Class.md),                         [IPersistPropertyBagImpl](../VS_visualcpp/IPersistPropertyBagImpl-Class.md),                         [IPersistStreamInitImpl](../VS_visualcpp/IPersistStreamInitImpl-Class.md), and                         [ISpecifyPropertyPagesImpl](../VS_visualcpp/ISpecifyPropertyPagesImpl-Class.md) use the property map to retrieve and set this information.  
  
 When you create an object with the ATL Project Wizard, the wizard will create an empty property map by specifying                         `BEGIN_PROP_MAP` followed by                         [END_PROP_MAP](../Topic/END_PROP_MAP.md).  
  
 `BEGIN_PROP_MAP` does not save out the extent (that is, the dimensions) of a property map, because an object using a property map may not have a user interface, so it would have no extent. If the object is an ActiveX control with a user interface, it has an extent. In this case, you must specify                         [PROP_DATA_ENTRY](../Topic/PROP_DATA_ENTRY.md) in your property map to supply the extent.  
  
### Example  
 [!CODE [NVC_ATL_Windowing#103](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Windowing#103)]  
  
##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY  
 Indicates the extent, or dimensions, of an ActiveX control.  
  
```  
  
PROP_DATA_ENTRY(Â   
   szDesc  
,Â   
   member  
,Â   
   vt Â   
)  
  
```  
  
### Parameters  
 `szDesc`  
 [in] The property description.  
  
 `member`  
 [in] The data member containing the extent; for example,                                 `m_sizeExtent`.  
  
 *vt*  
 [in] Specifies the VARIANT type of the property.  
  
### Remarks  
 This macro causes the specified data member to be persisted.  
  
 When you create an ActiveX control, the wizard inserts this macro after the property map macro                         [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md) and before the property map macro                         [END_PROP_MAP](../Topic/END_PROP_MAP.md).  
  
### Example  
 In the following example, the extent of the object (                                `m_sizeExtent`) is being persisted.  
  
 [!CODE [NVC_ATL_Windowing#131](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Windowing#131)]  
  
 [!CODE [NVC_ATL_Windowing#132](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Windowing#132)]  
  
##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE  
 Use this macro to enter a property description, property DISPID, and property page CLSID into the object's property map.  
  
```  
PROP_ENTRY_TYPE(Â   
                   szDesc,Â   
                   dispid,Â   
                   clsid,Â   
                   vtÂ   
)  
```  
  
### Parameters  
 `szDesc`  
 [in] The property description.  
  
 `dispid`  
 [in] The property's DISPID.  
  
 `clsid`  
 [in] The CLSID of the associated property page. Use the special value                                 `CLSID_NULL` for a property that does not have an associated property page.  
  
 `vt`  
 [in] The property's type.  
  
### Remarks  
 The                         `PROP_ENTRY` macro was insecure and deprecated. It has been replaced with                         `PROP_ENTRY_TYPE`.  
  
 The                         [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md) macro marks the beginning of the property map; the                         [END_PROP_MAP](../Topic/END_PROP_MAP.md) macro marks the end.  
  
### Example  
 See the example for                                 [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md).  
  
##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX  
 Similar to                 [PROP_ENTRY_TYPE](../Topic/PROP_ENTRY_TYPE.md), but allows you specify a particular IID if your object supports multiple dual interfaces.  
  
```  
PROP_ENTRY_TYPE_EX(Â   
                   szDesc,Â   
                   dispid,Â   
                   clsid,Â   
                   iidDispatch,Â   
                   vtÂ   
)  
```  
  
### Parameters  
 `szDesc`  
 [in] The property description.  
  
 `dispid`  
 [in] The property's DISPID.  
  
 `clsid`  
 [in] The CLSID of the associated property page. Use the special value                                 `CLSID_NULL` for a property that does not have an associated property page.  
  
 `iidDispatch`  
 [in] The IID of the dual interface defining the property.  
  
 `vt`  
 [in] The property's type.  
  
### Remarks  
 The                         `PROP_ENTRY_EX` macro was insecure and deprecated. It has been replaced with                         `PROP_ENTRY_TYPE_EX`.  
  
 The                         [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md) macro marks the beginning of the property map; the                         [END_PROP_MAP](../Topic/END_PROP_MAP.md) macro marks the end.  
  
### Example  
 The following example groups entries for                                 `IMyDual1` followed by an entry for                                 `IMyDual2`. Grouping by dual interface will improve performance.  
  
 [!CODE [NVC_ATL_Windowing#133](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Windowing#133)]  
  
##  <a name="prop_page"></a>  PROP_PAGE  
 Use this macro to enter a property page CLSID into the object's property map.  
  
```  
  
PROP_PAGE(Â   
   clsid Â   
)  
  
```  
  
### Parameters  
 `clsid`  
 [in] The CLSID of a property page.  
  
### Remarks  
 `PROP_PAGE` is similar to                         [PROP_ENTRY_TYPE](../Topic/PROP_ENTRY_TYPE.md), but does not require a property description or DISPID.  
  
> [!NOTE]
>  If you have already entered a CLSID with                             `PROP_ENTRY_TYPE` or                             [PROP_ENTRY_TYPE_EX](../Topic/PROP_ENTRY_TYPE_EX.md), you do not need to make an additional entry with                             `PROP_PAGE`.  
  
 The                         [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md) macro marks the beginning of the property map; the                         [END_PROP_MAP](../Topic/END_PROP_MAP.md) macro marks the end.  
  
### Example  
 [!CODE [NVC_ATL_Windowing#134](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Windowing#134)]  
  
##  <a name="end_prop_map"></a>  END_PROP_MAP  
 Marks the end of the object's property map.  
  
```  
  
END_PROP_MAP( )  
  
```  
  
### Remarks  
 When you create an object with the ATL Project Wizard, the wizard will create an empty property map by specifying                         [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md) followed by                         `END_PROP_MAP`.  
  
### Example  
 See the example for                                 [BEGIN_PROP_MAP](../Topic/BEGIN_PROP_MAP.md).  
  
## See Also  
 [Macros](../VS_visualcpp/ATL-Macros.md)