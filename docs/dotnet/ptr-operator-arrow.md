---
title: "ptr::operator-&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology:  
  - "cpp-windows"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.com.ptr.operator->"
  - "ptr.operator->"
  - "ptr::operator->"
  - "msclr::com::ptr::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::operator->"
ms.assetid: e752b549-74ed-430d-9a60-6c8e0e441998
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# ptr::operator-&gt;
Member access operator, used to call methods on the owned COM object.  
  
## Syntax  
  
```  
_detail::smart_com_ptr<_interface_type> operator->();  
```  
  
## Return Value  
 A `smart_com_ptr` to the COM object.  
  
## Exceptions  
 Internally, `QueryInterface` is called on the owned COM object and any error `HRESULT` is converted to an exception by <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.  
  
## Remarks  
 This operator allows you to call methods of the owned COM object. It returns a temporary `smart_com_ptr` that automatically handles its own `AddRef` and `Release`.  
  
## Example  
 This example implements a CLR class that uses a `com::ptr` to wrap its private member `IXMLDOMDocument` object. The `WriteDocument` functions uses `operator->` to call the `get_firstChild` member of the document object.  
  
```  
// comptr_op_member.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
  
   // add a reference to and return the COM object  
   // but keep an internal reference to the object  
   IXMLDOMDocument* GetDocument() {  
      return m_ptrDoc.GetInterface();  
   }  
  
   // simplified function that only writes the first node  
   void WriteDocument() {  
      IXMLDOMNode* pNode = NULL;  
      BSTR bstr = NULL;  
  
      try {  
         // use operator -> to call XML Doc member  
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));  
         if (NULL != pNode) {  
            // write out the xml  
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));  
            String^ strName = gcnew String(bstr);  
            Console::Write("<{0}>", strName);  
            ::SysFreeString(bstr);  
            bstr = NULL;  
  
            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));  
            Console::Write(gcnew String(bstr));  
            ::SysFreeString(bstr);  
            bstr = NULL;  
  
            Console::WriteLine("</{0}>", strName);  
         }  
      }  
      finally {  
         if (NULL != pNode) {  
            pNode->Release();  
         }  
         ::SysFreeString(bstr);  
      }  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// unmanaged function that loads XML into a raw XML DOM Document object  
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {  
   HRESULT hr = S_OK;  
   VARIANT_BOOL bSuccess;  
   hr = pDoc->loadXML(bstrXml, &bSuccess);  
   if (S_OK == hr && !bSuccess) {  
      hr = E_FAIL;  
   }  
   return hr;  
}  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
   BSTR bstrXml = NULL;  
  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      bstrXml = ::SysAllocString(L"<word>persnickety</word>");  
      if (NULL == bstrXml) {  
         throw gcnew OutOfMemoryException("bstrXml");  
      }  
      // detach the document object from the ref class  
      pDoc = doc.GetDocument();  
      // use unmanaged function and raw object to load xml  
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));  
      // release reference to document object (but ref class still references it)  
      pDoc->Release();  
      pDoc = NULL;  
  
      // call another function on the ref class  
      doc.WriteDocument();  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
   finally {  
      if (NULL != pDoc) {  
         pDoc->Release();  
      }  
  
   }  
}  
```  
  
```Output  
<word>persnickety</word>  
```  
  
## Requirements  
 **Header file** \<msclr\com\ptr.h>  
  
 **Namespace** msclr::com  
  
## See Also  
 [ptr Members](../dotnet/ptr-members.md)