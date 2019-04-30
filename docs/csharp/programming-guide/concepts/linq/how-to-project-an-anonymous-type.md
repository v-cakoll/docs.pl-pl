---
title: 'Instrukcje: Projektowanie typu anonimowego (C#)'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: d19fd40b213280523d0d731e5e3e8ba5213bcd49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701843"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Instrukcje: Projektowanie typu anonimowego (C#)
W niektórych przypadkach możesz chcieć projektu zapytania do nowego typu, nawet jeśli wiesz, że tego typu będą używać tylko przez krótki czas. Jest dużo dodatkową pracę, aby utworzyć nowy typ tylko do użycia w projekcji. W tym przypadku jest bardziej wydajne podejście projektu do typu anonimowego. Typy anonimowe umożliwiają definiowanie klasy, a następnie zadeklarowania i zainicjowania obiektu tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe są implementacji języka C# matematyczne koncepcji *krotki*. Krotka matematyczne termin pochodzi z sekwencji jednego, double, triple, czterokrotnie, pięciokrotnie, spójnej kolekcji n. Dotyczy skończonej sekwencji obiektów, każdy z określonego typu. Jest to czasami nazywane listą par nazwa/wartość. Na przykład zawartość adresu w [przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) dokumentu XML, które mogą być wyrażone w następujący sposób:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego jest wygodne należy traktować go jako tworzenia spójnej kolekcji n zamówienia. Jeśli piszesz zapytanie, które tworzy spójną kolekcję w `select` klauzuli zapytanie zwraca `IEnumerable` spójnej kolekcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `select` klauzuli projektów typu anonimowego. Następnie w przykładzie `var` utworzyć `IEnumerable` obiektu. W ramach `foreach` staje się Zmienna iteracji pętli, wystąpienie typu anonimowego, utworzone w wyrażeniu zapytania.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
