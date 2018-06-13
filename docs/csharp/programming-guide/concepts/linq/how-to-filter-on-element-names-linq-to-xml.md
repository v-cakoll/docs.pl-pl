---
title: 'Porady: Filtr na nazwy elementów (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: f54b9008ff90922e2c275c51c6965c92cb4e6a36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323264"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a>Porady: Filtr na nazwy elementów (LINQ do XML) (C#)
Jeśli wywołasz jednej z metod, które zwracają <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można filtrować według nazwy elementu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pobiera kolekcję elementów podrzędnych jest filtrowana zawiera tylko elementy podrzędne o określonej nazwie.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Inne metody, które zwracają <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekcje wykonują te same czynności. Ich sygnaturach są podobne do <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>. Oto pełną listę metod, które mają podobne podpisy metod:  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
