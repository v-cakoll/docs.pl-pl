---
title: Grupowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635746"
---
# <a name="grouping-data-c"></a>Grupowanie danych (C#)
Grupowanie odnosi się do działania umieszczania danych w grupach, tak aby elementy w każdej grupie współużytkują wspólny atrybut.  
  
 Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków. Kluczem dla każdej grupy jest znak.  
  
 ![Diagram, który pokazuje operację linq grupowanie.](./media/grouping-data/linq-group-operation.png)  
  
 Standardowe metody operatora kwerendy, które grupują elementy danych są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Grupje elementy, które mają wspólny atrybut. Każda grupa jest reprezentowana przez obiekt. <xref:System.Linq.IGrouping%602>|`group … by`<br /><br /> — lub —<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|Tolookup|Wstawia elementy <xref:System.Linq.Lookup%602> do (słownik jeden-do-wielu) na podstawie funkcji selektora kluczy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia kwerendy  
 Poniższy przykład kodu `group by` używa klauzuli do grupowania liczb całkowitych na liście w zależności od tego, czy są one parzyste, czy nieparzyste.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [group, klauzula](../../../language-reference/keywords/group-clause.md)
- [Tworzenie grupy zagnieżdżonej](../../../linq/create-a-nested-group.md)
- [Jak grupować pliki według rozszerzenia (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Grupowanie wyników zapytania](../../../linq/group-query-results.md)
- [Wykonywanie podzapytania w operacji grupowania](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
