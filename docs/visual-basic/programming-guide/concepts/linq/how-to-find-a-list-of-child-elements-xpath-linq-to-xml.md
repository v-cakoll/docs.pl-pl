---
title: 'Instrukcje: Znajdowanie listy elementów podrzędnych (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: 899252e7aacdec00ad75611ee4d149a53e71f95e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353007"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie listy elementów podrzędnych (XPath-LINQ to XML) (Visual Basic)
W tym temacie porównano oś elementów podrzędnych XPath z osią [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.  
  
 Wyrażenie XPath jest: `./*`  
  
## <a name="example"></a>Przykład  
 Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych elementu `Address`.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
