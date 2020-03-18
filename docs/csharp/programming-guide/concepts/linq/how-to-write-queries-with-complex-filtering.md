---
title: Jak pisać zapytania ze złożonym filtrowaniem (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: bc85d7f1e5c5305407ad22f3ada908523313d964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168521"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Jak pisać zapytania ze złożonym filtrowaniem (C#)
Czasami chcesz napisać LINQ do zapytań XML ze złożonymi filtrami. Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości. W tym temacie podano przykład pisania kwerendy ze złożonym filtrowaniem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak `PurchaseOrder` `Address` znaleźć wszystkie `Type` elementy, które mają element `State` podrzędny, który ma atrybut równy "Wysyłka" i element podrzędny równy "NY". Używa zagnieżdżonej kwerendy `Any` w `true` klauzuli, `Where` a operator zwraca, jeśli kolekcja ma żadnych elementów w nim. Aby uzyskać informacje dotyczące używania składni kwerend opartych na metodach, zobacz [Składnia kwerend i Składnia metody w pliku LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)  
  
 Aby uzyskać więcej `Any` informacji na temat operatora, zobacz [Operacje kwantyfikatora (C#)](./quantifier-operations.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
99505  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu w obszarze nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
99505  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Operacje projekcji (C#)](./projection-operations.md)
- [Operacje kwantyfikatora (C#)](./quantifier-operations.md)
