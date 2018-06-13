---
title: 'Porady: znajdowanie elementem głównym (XPath-LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 112be85e8af8fbe31f62ef91db04de72a3793082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641092"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>Porady: znajdowanie elementem głównym (XPath-LINQ do XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać elementu głównego z XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Wyrażenie XPath jest:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie znajduje elementu głównego.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
