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
# <a name="how-to-project-an-anonymous-type-c"></a>Jak projektować typ anonimowy (C#)
W niektórych przypadkach warto zaprojektować zapytanie do nowego typu, nawet jeśli wiesz, że ten typ będzie używany tylko przez krótki czas. Jest to wiele dodatkowych nakładów pracy, aby utworzyć nowy typ tylko do użycia w projekcji. Wydajniejszym rozwiązaniem w tym przypadku jest zaprojektowanie typu anonimowego. Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarowanie i zainicjowanie obiektu tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe to implementacja języka C# koncepcji matematycznej *krotki*. "Wyrażenie matematyczne" pochodziło z sekwencji pojedynczej, podwójnej, potrójnej, czterokrotnej, Quintuple, n-krotki. Odnosi się do skończonej sekwencji obiektów, każdego określonego typu. Czasami jest to nazywane listą par nazwa/wartość. Na przykład zawartość adresu w [przykładowym pliku XML: typowy dokument XML zamówienia zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) można wyrazić w następujący sposób:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest go traktować jak tworzenie spójnej kolekcji Order n. Jeśli napiszesz zapytanie, które tworzy krotkę w `select` klauzuli, zapytanie zwraca `IEnumerable` kolekcję.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `select` klauzula projektuje typ anonimowy. Przykład używa `var` do tworzenia `IEnumerable` obiektu. W `foreach` pętli Zmienna iteracji zostaje wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Ten kod spowoduje wygenerowanie następujących danych wyjściowych:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  