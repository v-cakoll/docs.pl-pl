---
title: 'Instrukcje: Zapisuj zapytania ze złożonym filtrowaniemC#()'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 08c1e124542e6d7e4c728102b2aa7fb4a804794c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710042"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="f48b5-102">Instrukcje: Zapisuj zapytania ze złożonym filtrowaniemC#()</span><span class="sxs-lookup"><span data-stu-id="f48b5-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="f48b5-103">Czasami chcesz pisać zapytania LINQ to XML ze złożonymi filtrami.</span><span class="sxs-lookup"><span data-stu-id="f48b5-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="f48b5-104">Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="f48b5-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="f48b5-105">Ten temat zawiera przykład tworzenia zapytania z skomplikowanym filtrowaniem.</span><span class="sxs-lookup"><span data-stu-id="f48b5-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f48b5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f48b5-106">Example</span></span>  
 <span data-ttu-id="f48b5-107">Ten przykład pokazuje, jak znaleźć wszystkie `PurchaseOrder` elementy, które mają element `Address` podrzędny, który ma `Type` atrybut równy "wysyłce" i element podrzędny `State` równy "NY".</span><span class="sxs-lookup"><span data-stu-id="f48b5-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="f48b5-108">Używa zapytania zagnieżdżonego w `Where` klauzuli `Any` i operator zwraca `true` , jeśli kolekcja zawiera jakiekolwiek elementy.</span><span class="sxs-lookup"><span data-stu-id="f48b5-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="f48b5-109">Aby uzyskać informacje o używaniu składni zapytania opartej na metodzie, zobacz [składnia zapytań i składnia metod w LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f48b5-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="f48b5-110">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f48b5-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f48b5-111">Aby uzyskać więcej informacji na `Any` temat operatora, zobacz [Operacje kwantyfikatoraC#()](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f48b5-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="f48b5-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f48b5-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="f48b5-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f48b5-113">Example</span></span>  
 <span data-ttu-id="f48b5-114">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f48b5-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f48b5-115">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f48b5-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f48b5-116">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu w przestrzeni nazw](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f48b5-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="f48b5-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f48b5-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="f48b5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f48b5-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="f48b5-119">Operacje projekcjiC#()</span><span class="sxs-lookup"><span data-stu-id="f48b5-119">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="f48b5-120">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="f48b5-120">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
