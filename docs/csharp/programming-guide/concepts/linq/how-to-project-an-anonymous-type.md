---
title: 'Instrukcje: Projektowanie typu anonimowego (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 68b008d70474c927a7911dc77e60afb634035b77
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485129"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="ee167-102">Instrukcje: Projektowanie typu anonimowego (C#)</span><span class="sxs-lookup"><span data-stu-id="ee167-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="ee167-103">W niektórych przypadkach możesz chcieć projektu zapytania do nowego typu, nawet jeśli wiesz, że tego typu będą używać tylko przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="ee167-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="ee167-104">Jest dużo dodatkową pracę, aby utworzyć nowy typ tylko do użycia w projekcji.</span><span class="sxs-lookup"><span data-stu-id="ee167-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="ee167-105">W tym przypadku jest bardziej wydajne podejście projektu do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="ee167-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="ee167-106">Typy anonimowe umożliwiają definiowanie klasy, a następnie zadeklarowania i zainicjowania obiektu tej klasy bez podawania nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="ee167-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="ee167-107">Typy anonimowe są implementacji języka C# matematyczne koncepcji *krotki*.</span><span class="sxs-lookup"><span data-stu-id="ee167-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="ee167-108">Krotka matematyczne termin pochodzi z sekwencji jednego, double, triple, czterokrotnie, pięciokrotnie, spójnej kolekcji n.</span><span class="sxs-lookup"><span data-stu-id="ee167-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="ee167-109">Dotyczy skończonej sekwencji obiektów, każdy z określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ee167-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="ee167-110">Jest to czasami nazywane listą par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="ee167-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="ee167-111">Na przykład zawartość adresu w [przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokumentu XML, które mogą być wyrażone w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee167-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="ee167-112">Podczas tworzenia wystąpienia typu anonimowego jest wygodne należy traktować go jako tworzenia spójnej kolekcji n zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ee167-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="ee167-113">Jeśli piszesz zapytanie, które tworzy spójną kolekcję w `select` klauzuli zapytanie zwraca `IEnumerable` spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ee167-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee167-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee167-114">Example</span></span>  
 <span data-ttu-id="ee167-115">W tym przykładzie `select` klauzuli projektów typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="ee167-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="ee167-116">Następnie w przykładzie `var` utworzyć `IEnumerable` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ee167-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="ee167-117">W ramach `foreach` staje się Zmienna iteracji pętli, wystąpienie typu anonimowego, utworzone w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="ee167-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="ee167-118">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="ee167-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="ee167-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ee167-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  