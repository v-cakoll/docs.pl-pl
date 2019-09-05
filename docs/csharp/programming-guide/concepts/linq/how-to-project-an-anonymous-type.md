---
title: 'Instrukcje: Zaprojektuj typ anonimowyC#()'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 3ed14ae6e7bc4b84ae9dc416b76e37443b831c73
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253493"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Instrukcje: Zaprojektuj typ anonimowyC#()
W niektórych przypadkach warto zaprojektować zapytanie do nowego typu, nawet jeśli wiesz, że ten typ będzie używany tylko przez krótki czas. Jest to wiele dodatkowych nakładów pracy, aby utworzyć nowy typ tylko do użycia w projekcji. Wydajniejszym rozwiązaniem w tym przypadku jest zaprojektowanie typu anonimowego. Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarowanie i zainicjowanie obiektu tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe są C# implementacją koncepcji matematycznej *krotki*. "Wyrażenie matematyczne" pochodziło z sekwencji pojedynczej, podwójnej, potrójnej, czterokrotnej, Quintuple, n-krotki. Odnosi się do skończonej sekwencji obiektów, każdego określonego typu. Czasami jest to nazywane listą par nazwa/wartość. Na przykład zawartość adresu w [przykładowym pliku XML: Typowy dokument XML zamówienia zakupu (](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) LINQ to XML) można wyrazić w następujący sposób:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest go traktować jak tworzenie spójnej kolekcji Order n. Jeśli napiszesz zapytanie, które tworzy krotkę w `select` klauzuli, zapytanie `IEnumerable` zwraca kolekcję.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `select` klauzula projektuje typ anonimowy. Przykład używa `var` do `IEnumerable` tworzenia obiektu. `foreach` W pętli Zmienna iteracji zostaje wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  