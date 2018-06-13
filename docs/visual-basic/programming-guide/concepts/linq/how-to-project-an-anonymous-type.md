---
title: 'Porady: projekt typu anonimowego (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: 13500bc606cb99a4264e04657f4a0a8090f07174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643587"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>Porady: projekt typu anonimowego (Visual Basic)
W niektórych przypadkach można projektu zapytania do nowego typu, nawet jeśli wiadomo, że ten typ będzie używać tylko przez krótki czas. Istnieje wiele dodatkowej pracy, aby utworzyć nowy typ tylko do użycia w projekcji. W takim przypadku jest bardziej wydajne rozwiązanie projektu do typu anonimowego. Typy anonimowe umożliwiają definiowanie klasy, a następnie deklarowanie i zainicjowania obiektu dla tej klasy bez podawania nazwy klasy.  
  
 Typy anonimowe są implementacji C# matematyczne pojęcia *krotki*. Tuple matematyczne termin pochodzi od sekwencji pojedynczego, double, triple, poczwórnej, pięciokrotnie, n-spójnej kolekcji. Odnosi się do sekwencji skończoną obiektów, każdego programu określonego typu. Czasami jest to Lista par nazwa/wartość. Na przykład zawartość adresu [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) dokument XML, które mogą być wyrażone w następujący sposób:  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 Podczas tworzenia wystąpienia typu anonimowego jest wygodne go traktować jako tworzenie krotka n kolejności. Jeśli Napisz zapytanie, które tworzy krotka w `Select` klauzuli, gdy kwerenda zwraca `IEnumerable` z spójnej kolekcji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Select` klauzuli projektów typu anonimowego. W przykładzie następnie użyto `Dim` utworzyć `IEnumerable` obiektu. W ramach `For Each` staje się zmiennej iteracji pętli, wystąpienie typu anonimowego utworzone w wyrażeniu zapytania.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Projekcje i przekształcenia (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
