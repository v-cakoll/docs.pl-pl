---
title: 'Instrukcje: Pisanie zapytań z zaawansowanym filtrowaniem (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 847e50cf0c1cf91f8b731457d351bb0d01d725c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700588"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="6f31d-102">Instrukcje: Pisanie zapytań z zaawansowanym filtrowaniem (C#)</span><span class="sxs-lookup"><span data-stu-id="6f31d-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="6f31d-103">Czasami chcesz zapisywać LINQ do XML zapytań za pomocą złożonych filtrów.</span><span class="sxs-lookup"><span data-stu-id="6f31d-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="6f31d-104">Na przykład trzeba znaleźć wszystkie elementy, które ma element podrzędny o określonej nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="6f31d-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="6f31d-105">Ten temat zawiera przykładowy Pisanie zapytań z zaawansowanym filtrowaniem.</span><span class="sxs-lookup"><span data-stu-id="6f31d-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f31d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f31d-106">Example</span></span>  
 <span data-ttu-id="6f31d-107">W tym przykładzie pokazano, jak znaleźć wszystkie `PurchaseOrder` elementy podrzędne `Address` element, który ma `Type` atrybutu jest równa "Wysyłania" i elementem podrzędnym `State` element równy "NY".</span><span class="sxs-lookup"><span data-stu-id="6f31d-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="6f31d-108">Używa ona zapytanie zagnieżdżone w `Where` klauzuli i `Any` operator zwraca `true` Jeśli kolekcja zawiera żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="6f31d-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="6f31d-109">Aby dowiedzieć się, jak za pomocą składni zapytania oparte na metodzie, zobacz [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="6f31d-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="6f31d-110">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6f31d-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6f31d-111">Aby uzyskać więcej informacji na temat `Any` operatora, zobacz [Operacje kwantyfikatora (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6f31d-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="6f31d-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6f31d-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="6f31d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f31d-113">Example</span></span>  
 <span data-ttu-id="6f31d-114">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6f31d-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6f31d-115">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6f31d-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="6f31d-116">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6f31d-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="6f31d-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6f31d-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f31d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f31d-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="6f31d-119">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6f31d-119">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="6f31d-120">Operacje rzutowania (C#)</span><span class="sxs-lookup"><span data-stu-id="6f31d-120">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="6f31d-121">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="6f31d-121">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
