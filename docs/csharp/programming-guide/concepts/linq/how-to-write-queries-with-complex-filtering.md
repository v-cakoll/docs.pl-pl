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
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="d0e1f-102">Jak pisać zapytania ze złożonym filtrowaniem (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1f-102">How to write queries with complex filtering (C#)</span></span>
<span data-ttu-id="d0e1f-103">Czasami chcesz napisać LINQ do zapytań XML ze złożonymi filtrami.</span><span class="sxs-lookup"><span data-stu-id="d0e1f-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="d0e1f-104">Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="d0e1f-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="d0e1f-105">W tym temacie podano przykład pisania kwerendy ze złożonym filtrowaniem.</span><span class="sxs-lookup"><span data-stu-id="d0e1f-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0e1f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0e1f-106">Example</span></span>  
 <span data-ttu-id="d0e1f-107">W tym przykładzie pokazano, jak `PurchaseOrder` `Address` znaleźć wszystkie `Type` elementy, które mają element `State` podrzędny, który ma atrybut równy "Wysyłka" i element podrzędny równy "NY".</span><span class="sxs-lookup"><span data-stu-id="d0e1f-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="d0e1f-108">Używa zagnieżdżonej kwerendy `Any` w `true` klauzuli, `Where` a operator zwraca, jeśli kolekcja ma żadnych elementów w nim.</span><span class="sxs-lookup"><span data-stu-id="d0e1f-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="d0e1f-109">Aby uzyskać informacje dotyczące używania składni kwerend opartych na metodach, zobacz [Składnia kwerend i Składnia metody w pliku LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d0e1f-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="d0e1f-110">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="d0e1f-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d0e1f-111">Aby uzyskać więcej `Any` informacji na temat operatora, zobacz [Operacje kwantyfikatora (C#)](./quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d0e1f-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="d0e1f-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d0e1f-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="d0e1f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0e1f-113">Example</span></span>  
 <span data-ttu-id="d0e1f-114">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="d0e1f-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d0e1f-115">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d0e1f-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d0e1f-116">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu w obszarze nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d0e1f-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="d0e1f-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d0e1f-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0e1f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0e1f-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="d0e1f-119">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1f-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="d0e1f-120">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1f-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
