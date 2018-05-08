---
title: 'Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 664b9496c8411055fcd09a1ea0709cdfdae79524
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (C#)
W tym temacie wyjaśniono, jak pobrać element pojedynczy element potomny, nazwę elementu podrzędnego. Jeśli znasz nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie, może być wygodną można pobrać tylko jeden element, zamiast kolekcji.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.  
  
 Jeśli chcesz pobrać pojedynczym elemencie podrzędnym w języku Visual Basic, typowym podejściem jest przy użyciu właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody. W tym przykładzie przyjmuje drzewa XML o nazwie `po` i klient znajdzie pierwszy element o nazwie `Comment`.  
  
 W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy można pobrać pojedynczy element.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
 Poniższy przykład przedstawia ten sam kod XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
