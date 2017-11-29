---
title: 'Porady: projekt typu anonimowego (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7b56e919342cb168951c78a2d90953ba0ab758c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="76f23-102">Porady: projekt typu anonimowego (C#)</span><span class="sxs-lookup"><span data-stu-id="76f23-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="76f23-103">W niektórych przypadkach można projektu zapytania do nowego typu, nawet jeśli wiadomo, że ten typ będzie używać tylko przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="76f23-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="76f23-104">Istnieje wiele dodatkowej pracy, aby utworzyć nowy typ tylko do użycia w projekcji.</span><span class="sxs-lookup"><span data-stu-id="76f23-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="76f23-105">W takim przypadku jest bardziej wydajne rozwiązanie projektu do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="76f23-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="76f23-106">Typy anonimowe umożliwiają definiowanie klasy, a następnie deklarowanie i zainicjowania obiektu dla tej klasy bez podawania nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="76f23-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="76f23-107">Typy anonimowe są implementacji C# matematyczne pojęcia *krotki*.</span><span class="sxs-lookup"><span data-stu-id="76f23-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="76f23-108">Tuple matematyczne termin pochodzi od sekwencji pojedynczego, double, triple, poczwórnej, pięciokrotnie, n-spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76f23-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="76f23-109">Odnosi się do sekwencji skończoną obiektów, każdego programu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="76f23-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="76f23-110">Czasami jest to Lista par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="76f23-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="76f23-111">Na przykład zawartość adresu [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokument XML, które mogą być wyrażone w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76f23-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="76f23-112">Podczas tworzenia wystąpienia typu anonimowego jest wygodne go traktować jako tworzenie krotka n kolejności.</span><span class="sxs-lookup"><span data-stu-id="76f23-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="76f23-113">Jeśli Napisz zapytanie, które tworzy krotka w `select` klauzuli, gdy kwerenda zwraca `IEnumerable` z spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76f23-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76f23-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="76f23-114">Example</span></span>  
 <span data-ttu-id="76f23-115">W tym przykładzie `select` klauzuli projektów typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="76f23-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="76f23-116">W przykładzie następnie użyto `var` utworzyć `IEnumerable` obiektu.</span><span class="sxs-lookup"><span data-stu-id="76f23-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="76f23-117">W ramach `foreach` staje się zmiennej iteracji pętli, wystąpienie typu anonimowego utworzone w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="76f23-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="76f23-118">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="76f23-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="76f23-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="76f23-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="76f23-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76f23-120">See Also</span></span>  
 [<span data-ttu-id="76f23-121">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76f23-121">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
