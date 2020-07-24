---
title: Jak projektować typ anonimowy (C#)
description: Dowiedz się, jak projektować zapytanie do typu anonimowego w języku C#. Korzystanie z typu anonimowego może być łatwiejsze niż tworzenie nowego typu do użycia tylko w skrócie.
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104636"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="b6404-104">Jak projektować typ anonimowy (C#)</span><span class="sxs-lookup"><span data-stu-id="b6404-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="b6404-105">W niektórych przypadkach warto zaprojektować zapytanie do nowego typu, nawet jeśli wiesz, że ten typ będzie używany tylko przez krótki czas.</span><span class="sxs-lookup"><span data-stu-id="b6404-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="b6404-106">Jest to wiele dodatkowych nakładów pracy, aby utworzyć nowy typ tylko do użycia w projekcji.</span><span class="sxs-lookup"><span data-stu-id="b6404-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="b6404-107">Wydajniejszym rozwiązaniem w tym przypadku jest zaprojektowanie typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="b6404-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="b6404-108">Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarowanie i zainicjowanie obiektu tej klasy bez podawania nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="b6404-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="b6404-109">Typy anonimowe to implementacja języka C# koncepcji matematycznej *krotki*.</span><span class="sxs-lookup"><span data-stu-id="b6404-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="b6404-110">"Wyrażenie matematyczne" pochodziło z sekwencji pojedynczej, podwójnej, potrójnej, czterokrotnej, Quintuple, n-krotki.</span><span class="sxs-lookup"><span data-stu-id="b6404-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="b6404-111">Odnosi się do skończonej sekwencji obiektów, każdego określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b6404-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="b6404-112">Czasami jest to nazywane listą par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="b6404-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="b6404-113">Na przykład zawartość adresu w [przykładowym pliku XML: typowy dokument XML zamówienia zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) można wyrazić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b6404-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="b6404-114">Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest go traktować jak tworzenie spójnej kolekcji Order n.</span><span class="sxs-lookup"><span data-stu-id="b6404-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="b6404-115">Jeśli napiszesz zapytanie, które tworzy krotkę w `select` klauzuli, zapytanie zwraca `IEnumerable` kolekcję.</span><span class="sxs-lookup"><span data-stu-id="b6404-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6404-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6404-116">Example</span></span>  
 <span data-ttu-id="b6404-117">W tym przykładzie `select` klauzula projektuje typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="b6404-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="b6404-118">Przykład używa `var` do tworzenia `IEnumerable` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b6404-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="b6404-119">W `foreach` pętli Zmienna iteracji zostaje wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6404-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="b6404-120">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="b6404-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="b6404-121">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="b6404-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  