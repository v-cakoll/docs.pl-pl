---
title: 'Instrukcje: Projektowanie typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: cc8e59ac1037fc173cb44d8c8ff344374c5766ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834572"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Instrukcje: Projektowanie typu anonimowego (Visual Basic)
W niektórych przypadkach możesz chcieć projektu zapytania do nowego typu, nawet jeśli wiesz, że tego typu będą używać tylko przez krótki czas. Jest dużo dodatkową pracę, aby utworzyć nowy typ tylko do użycia w projekcji. W tym przypadku jest bardziej wydajne podejście projektu do typu anonimowego. Typy anonimowe umożliwiają definiowanie klasy, a następnie zadeklarowania i zainicjowania obiektu tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe są implementacji języka C# matematyczne koncepcji *krotki*. Krotka matematyczne termin pochodzi z sekwencji jednego, double, triple, czterokrotnie, pięciokrotnie, spójnej kolekcji n. Dotyczy skończonej sekwencji obiektów, każdy z określonego typu. Jest to czasami nazywane listą par nazwa/wartość. Na przykład zawartość adresu w [przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokumentu XML, które mogą być wyrażone w następujący sposób:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego jest wygodne należy traktować go jako tworzenia spójnej kolekcji n zamówienia. Jeśli piszesz zapytanie, które tworzy spójną kolekcję w `Select` klauzuli zapytanie zwraca `IEnumerable` spójnej kolekcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Select` klauzuli projektów typu anonimowego. Następnie w przykładzie `Dim` utworzyć `IEnumerable` obiektu. W ramach `For Each` staje się Zmienna iteracji pętli, wystąpienie typu anonimowego, utworzone w wyrażeniu zapytania.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
