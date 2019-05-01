---
title: Grupowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: a85babc43f673711fe1bdfa5cec1836a5073c785
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807792"
---
# <a name="grouping-data-c"></a>Grupowanie danych (C#)
Grupowanie odnosi się do operacji umieszczania danych do grup, tak aby elementów w każdej grupie udostępniać wspólny atrybut.  
  
 Poniższa ilustracja przedstawia wyniki grupowania sekwencji znaków. Klucz dla każdej grupy jest znakiem.  
  
 ![Diagram przedstawiający operacji grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Metody standardowego operatora zapytań, które grupują elementy danych są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Grupuje elementy, które współużytkują wspólny atrybut. Każda grupa jest reprezentowany przez <xref:System.Linq.IGrouping%602> obiektu.|`group … by`<br /><br /> —lub—<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Wstawia elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 Poniższy przykład kodu wykorzystuje `group by` klauzuli grupy liczb całkowitych, na liście według tego, czy jest parzysta lub nieparzysta.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [group, klauzula](../../../../csharp/language-reference/keywords/group-clause.md)
- [Instrukcje: Tworzenie grup zagnieżdżonych](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [Instrukcje: Grupowanie plików według rozszerzenia (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [Instrukcje: Grupowanie wyników zapytania](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [Instrukcje: Wykonanie podzapytania w operacji grupowania](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
