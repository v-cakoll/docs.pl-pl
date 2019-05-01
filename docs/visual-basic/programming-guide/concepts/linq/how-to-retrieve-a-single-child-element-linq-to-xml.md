---
title: 'Instrukcje: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: e3b8c9d90f494330b30fe1b35a7fe64f882cae95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920201"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Instrukcje: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (Visual Basic)
W tym temacie wyjaśniono, jak pobrać jeden typ elementów podrzędnych, biorąc pod uwagę nazwę elementu podrzędnego. Znając nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie może być wygodna można pobrać tylko jeden element, zamiast kolekcji.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.  
  
 Jeśli chcesz pobrać jeden typ elementów podrzędnych w języku Visual Basic, typowym podejściem jest używać właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody. W tym przykładzie pobiera drzewa XML o nazwie `po` i znajdzie pierwszy element o nazwie `Comment`.  
  
 W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy, aby pobrać jeden element.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje ten sam kod XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
