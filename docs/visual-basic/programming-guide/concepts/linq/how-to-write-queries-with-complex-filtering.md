---
title: 'Instrukcje: pisanie zapytań z zaawansowanym filtrowaniem'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 18ed4379b7ec9c8007cc3c189fc45571b5161911
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397625"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Instrukcje: Pisanie zapytań ze złożonym filtrowaniem (Visual Basic)
Czasami chcesz pisać zapytania LINQ to XML ze złożonymi filtrami. Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości. Ten temat zawiera przykład tworzenia zapytania z skomplikowanym filtrowaniem.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak znaleźć wszystkie `PurchaseOrder` elementy, które mają `Address` element podrzędny, który ma `Type` atrybut równy "wysyłce" i `State` element podrzędny równy "NY". Używa zapytania zagnieżdżonego w `Where` klauzuli i `Any` operator zwraca, `True` Jeśli kolekcja zawiera jakiekolwiek elementy.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Aby uzyskać więcej informacji na temat `Any` operatora, zobacz [Kwantyfikatory operacji (Visual Basic)](quantifier-operations.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
99505  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu w przestrzeni nazw](sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
99505  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Właściwości osi elementu podrzędnego XML](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [Właściwości osi atrybutu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [Właściwość wartości XML](../../../language-reference/xml-axis/xml-value-property.md)
- [Operacje projekcji (Visual Basic)](projection-operations.md)
- [Operacje kwantyfikatora (Visual Basic)](quantifier-operations.md)
