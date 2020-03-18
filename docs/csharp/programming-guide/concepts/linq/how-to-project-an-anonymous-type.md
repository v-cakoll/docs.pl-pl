---
title: Jak wyświetlać typ anonimowy (C#)
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 7797c8bfb12943af1ce7f975b170bf002aa7d6fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345732"
---
# <a name="how-to-project-an-anonymous-type-c"></a>Jak wyświetlać typ anonimowy (C#)
W niektórych przypadkach można rzutkwerendy do nowego typu, nawet jeśli wiadomo, że będzie używać tego typu tylko na krótki czas. Jest to dużo dodatkowej pracy, aby stworzyć nowy typ tylko do wykorzystania w projekcji. Bardziej efektywne podejście w tym przypadku jest do projektu do typu anonimowego. Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarować i zainicjować obiekt tej klasy, bez nadawania klasie nazwy.  
  
 Typy anonimowe są implementacją C# koncepcji matematycznej *krotki*. Termin matematyczny krotka pochodzi z sekwencji pojedynczej, podwójnej, potrójnej, czteroosobowej, kwintetu, n-krotki. Odnosi się do skończonej sekwencji obiektów, każdy określonego typu. Czasami jest to nazywane listą par nazw/wartości. Na przykład zawartość adresu w [przykładowym pliku XML: Typowy dokument XML (TYPOWE zamówienie zakupu (LINQ do XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) może być wyrażona w następujący sposób:  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest myśleć o nim jako o tworzeniu krotki rzędu n. Jeśli piszesz kwerendę, która `select` tworzy krotkę `IEnumerable` w klauzuli, kwerenda zwraca krotki.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `select` klauzula wyświetla typ anonimowy. Przykład następnie `var` używa do `IEnumerable` utworzenia obiektu. W `foreach` pętli zmienna iteracji staje się wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
  