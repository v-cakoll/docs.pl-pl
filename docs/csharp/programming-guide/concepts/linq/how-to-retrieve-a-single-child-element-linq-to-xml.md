---
title: Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347473"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)
W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny o nazwie elementu podrzędnego. Gdy znana jest nazwa elementu podrzędnego i istnieje tylko jeden element o tej nazwie, może być wygodne pobranie tylko jednego elementu, a nie kolekcji.  
  
 Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pierwszy <xref:System.Xml.Linq.XElement> podrzędny z określonym <xref:System.Xml.Linq.XName>.  
  
 Jeśli chcesz pobrać pojedynczy element podrzędny w Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji Array indeksator.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje użycie metody <xref:System.Xml.Linq.XContainer.Element%2A>. Ten przykład pobiera drzewo XML o nazwie `po` i odnajduje pierwszy element o nazwie `Comment`.  
  
 W Visual Basic przykładzie pokazano użycie notacji indeksatora Array do pobrania pojedynczego elementu.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
 W poniższym przykładzie przedstawiono ten sam kod dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
