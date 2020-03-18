---
title: Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347473"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)
W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny, biorąc pod uwagę nazwę elementu podrzędnego. Gdy znasz nazwę elementu podrzędnego i że istnieje tylko jeden element, który ma tę nazwę, może być wygodne do pobrania tylko jeden element, zamiast kolekcji.  
  
 Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pierwsze <xref:System.Xml.Linq.XElement> dziecko z <xref:System.Xml.Linq.XName>określonym .  
  
 Jeśli chcesz pobrać pojedynczy element podrzędny w języku Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji indeksatora tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono <xref:System.Xml.Linq.XContainer.Element%2A> użycie metody. W tym przykładzie przyjmuje `po` drzewo XML o `Comment`nazwie i znajduje pierwszy element o nazwie .  
  
 W przykładzie języka Visual Basic przedstawiono przy użyciu notacji indeksatora tablicy do pobierania pojedynczego elementu.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
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
 W poniższym przykładzie przedstawiono ten sam kod dla Języka XML, który znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu w obszarze nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
