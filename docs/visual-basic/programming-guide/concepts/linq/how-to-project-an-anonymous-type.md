---
title: 'Porady: projekt typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 13500bc606cb99a4264e04657f4a0a8090f07174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="4f8cf-102">Porady: projekt typu anonimowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f8cf-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="4f8cf-103">W niektórych przypadkach można projektu zapytania do nowego typu, nawet jeśli wiadomo, że ten typ będzie używać tylko przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="4f8cf-104">Istnieje wiele dodatkowej pracy, aby utworzyć nowy typ tylko do użycia w projekcji.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="4f8cf-105">W takim przypadku jest bardziej wydajne rozwiązanie projektu do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="4f8cf-106">Typy anonimowe umożliwiają definiowanie klasy, a następnie deklarowanie i zainicjowania obiektu dla tej klasy bez podawania nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="4f8cf-107">Typy anonimowe są implementacji C# matematyczne pojęcia *krotki*.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="4f8cf-108">Tuple matematyczne termin pochodzi od sekwencji pojedynczego, double, triple, poczwórnej, pięciokrotnie, n-spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="4f8cf-109">Odnosi się do sekwencji skończoną obiektów, każdego programu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="4f8cf-110">Czasami jest to Lista par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="4f8cf-111">Na przykład zawartość adresu [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokument XML, które mogą być wyrażone w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4f8cf-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="4f8cf-112">Podczas tworzenia wystąpienia typu anonimowego jest wygodne go traktować jako tworzenie krotka n kolejności.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="4f8cf-113">Jeśli Napisz zapytanie, które tworzy krotka w `Select` klauzuli, gdy kwerenda zwraca `IEnumerable` z spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f8cf-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f8cf-114">Example</span></span>  
 <span data-ttu-id="4f8cf-115">W tym przykładzie `Select` klauzuli projektów typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="4f8cf-116">W przykładzie następnie użyto `Dim` utworzyć `IEnumerable` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="4f8cf-117">W ramach `For Each` staje się zmiennej iteracji pętli, wystąpienie typu anonimowego utworzone w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="4f8cf-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="4f8cf-118">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4f8cf-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="4f8cf-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4f8cf-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f8cf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f8cf-120">See Also</span></span>  
 [<span data-ttu-id="4f8cf-121">Projekcje i przekształcenia (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f8cf-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
