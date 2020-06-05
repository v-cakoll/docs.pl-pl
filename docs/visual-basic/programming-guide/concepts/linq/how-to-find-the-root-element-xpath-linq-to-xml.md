---
title: 'Instrukcje: wyszukiwanie elementu głównego (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: d1a507f97954c62672689bae719f251fed9a298b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364516"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>Instrukcje: wyszukiwanie elementu głównego (XPath-LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać element główny przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Wyrażenie XPath:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie elementu głównego.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
```console  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to XML dla użytkowników XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
