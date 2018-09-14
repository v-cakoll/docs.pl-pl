---
title: 'Porady: pobieranie jeden typ elementów podrzędnych (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 77ccd56d1d131a740bb90ef4258ef35504f5e3cb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597884"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Porady: pobieranie jeden typ elementów podrzędnych (LINQ to XML) (C#)
W tym temacie wyjaśniono, jak pobrać jeden typ elementów podrzędnych, biorąc pod uwagę nazwę elementu podrzędnego. Znając nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie może być wygodna można pobrać tylko jeden element, zamiast kolekcji.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.  
  
 Jeśli chcesz pobrać jeden typ elementów podrzędnych w języku Visual Basic, typowym podejściem jest używać właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody. W tym przykładzie pobiera drzewa XML o nazwie `po` i znajdzie pierwszy element o nazwie `Comment`.  
  
 W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy, aby pobrać jeden element.  
  
 W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
 Poniższy przykład pokazuje ten sam kod XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Zobacz też

- [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
