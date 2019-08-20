---
title: 'Instrukcje: Zaprojektuj typ anonimowyC#()'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: cd05c0ad7ab5a683b95e110cb0b1bb75b8a1dd2a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593032"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="a75c7-102">Instrukcje: Zaprojektuj typ anonimowyC#()</span><span class="sxs-lookup"><span data-stu-id="a75c7-102">How to: Project an Anonymous Type (C#)</span></span>
<span data-ttu-id="a75c7-103">W niektórych przypadkach warto zaprojektować zapytanie do nowego typu, nawet jeśli wiesz, że ten typ będzie używany tylko przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="a75c7-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="a75c7-104">Jest to wiele dodatkowych nakładów pracy, aby utworzyć nowy typ tylko do użycia w projekcji.</span><span class="sxs-lookup"><span data-stu-id="a75c7-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="a75c7-105">Wydajniejszym rozwiązaniem w tym przypadku jest zaprojektowanie typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="a75c7-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="a75c7-106">Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarowanie i zainicjowanie obiektu tej klasy bez podawania nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="a75c7-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="a75c7-107">Typy anonimowe są C# implementacją koncepcji matematycznej *krotki*.</span><span class="sxs-lookup"><span data-stu-id="a75c7-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="a75c7-108">"Wyrażenie matematyczne" pochodziło z sekwencji pojedynczej, podwójnej, potrójnej, czterokrotnej, Quintuple, n-krotki.</span><span class="sxs-lookup"><span data-stu-id="a75c7-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="a75c7-109">Odnosi się do skończonej sekwencji obiektów, każdego określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a75c7-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="a75c7-110">Czasami jest to nazywane listą par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="a75c7-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="a75c7-111">Na przykład zawartość adresu w [przykładowym pliku XML: Typowy dokument XML zamówienia zakupu (](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) LINQ to XML) można wyrazić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a75c7-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="a75c7-112">Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest go traktować jak tworzenie spójnej kolekcji Order n.</span><span class="sxs-lookup"><span data-stu-id="a75c7-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="a75c7-113">Jeśli napiszesz zapytanie, które tworzy krotkę w `select` klauzuli, zapytanie `IEnumerable` zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="a75c7-113">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a75c7-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a75c7-114">Example</span></span>  
 <span data-ttu-id="a75c7-115">W tym przykładzie `select` klauzula projektuje typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="a75c7-115">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="a75c7-116">Przykład używa `var` do `IEnumerable` tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="a75c7-116">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="a75c7-117">`foreach` W pętli Zmienna iteracji zostaje wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="a75c7-117">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="a75c7-118">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a75c7-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="a75c7-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a75c7-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  