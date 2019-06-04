---
title: 'Instrukcje: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 609488bcb8a15218e7d058031d8ee87dbc67092f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486535"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Instrukcje: Pobierz jeden typ elementów podrzędnych (LINQ to XML) (C#)
W tym temacie wyjaśniono, jak pobrać jeden typ elementów podrzędnych, biorąc pod uwagę nazwę elementu podrzędnego. Znając nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie może być wygodna można pobrać tylko jeden element, zamiast kolekcji.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.  
  
 Jeśli chcesz pobrać jeden typ elementów podrzędnych w języku Visual Basic, typowym podejściem jest używać właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody. W tym przykładzie pobiera drzewa XML o nazwie `po` i znajdzie pierwszy element o nazwie `Comment`.  
  
 W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy, aby pobrać jeden element.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje ten sam kod XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Zobacz także

- [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
