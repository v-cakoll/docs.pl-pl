---
title: Jak pisać zapytania ze złożonym filtrowaniem (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: a4918631fed21967b402c5c56cfb8a211d44c139
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337360"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Jak pisać zapytania ze złożonym filtrowaniem (C#)
Czasami chcesz pisać zapytania LINQ to XML ze złożonymi filtrami. Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości. Ten temat zawiera przykład tworzenia zapytania z skomplikowanym filtrowaniem.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak znaleźć wszystkie `PurchaseOrder` elementy mające element podrzędny `Address`, który ma atrybut `Type` równy "wysyłce" i podrzędny element `State` równy "NY". Używa zagnieżdżonego zapytania w klauzuli `Where`, a operator `Any` zwraca `true`, jeśli kolekcja zawiera jakiekolwiek elementy. Aby uzyskać informacje o używaniu składni zapytania opartej na metodzie, zobacz [składnia zapytań i składnia metod w LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Aby uzyskać więcej informacji na temat operatora `Any`, zobacz [Operacje kwantyfikatoraC#()](./quantifier-operations.md).  
  
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
 W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu w przestrzeni nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Operacje projekcjiC#()](./projection-operations.md)
- [Operacje kwantyfikatora (C#)](./quantifier-operations.md)
