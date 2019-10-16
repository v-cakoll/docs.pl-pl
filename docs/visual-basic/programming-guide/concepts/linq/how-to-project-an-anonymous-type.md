---
title: 'Instrukcje: projekt typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 9a4498913cdcff0f813f184be18816e4dc5179b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321497"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Instrukcje: projekt typu anonimowego (Visual Basic)
W niektórych przypadkach warto zaprojektować zapytanie do nowego typu, nawet jeśli wiesz, że ten typ będzie używany tylko przez krótki czas. Jest to wiele dodatkowych nakładów pracy, aby utworzyć nowy typ tylko do użycia w projekcji. Wydajniejszym rozwiązaniem w tym przypadku jest zaprojektowanie typu anonimowego. Typy anonimowe umożliwiają zdefiniowanie klasy, a następnie zadeklarowanie i zainicjowanie obiektu tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe są C# implementacją koncepcji matematycznej *krotki*. "Wyrażenie matematyczne" pochodziło z sekwencji pojedynczej, podwójnej, potrójnej, czterokrotnej, Quintuple, n-krotki. Odnosi się do skończonej sekwencji obiektów, każdego określonego typu. Czasami jest to nazywane listą par nazwa/wartość. Na przykład zawartość adresu w [przykładowym pliku XML: typowy dokument XML zamówienia zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) można wyrazić w następujący sposób:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego, wygodnie jest go traktować jak tworzenie spójnej kolekcji Order n. Jeśli napiszesz zapytanie, które tworzy krotkę w klauzuli `Select`, zapytanie zwróci `IEnumerable` spójnej kolekcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klauzula `Select` projektuje typ anonimowy. Przykład używa `Dim` do utworzenia obiektu `IEnumerable`. W pętli `For Each` Zmienna iteracji zostaje wystąpieniem typu anonimowego utworzonego w wyrażeniu zapytania.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
