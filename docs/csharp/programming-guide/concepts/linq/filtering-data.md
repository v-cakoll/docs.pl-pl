---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: eb448c1c2ea6d9b3fcf0120043cafebc01cd3805
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418474"
---
# <a name="filtering-data-c"></a>Filtrowanie danych (C#)
Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek. Jest on również znany jako wybór.  
  
 Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków. Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Gdzie|Wybiera wartości, które są oparte na funkcji predykatu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 W poniższym przykładzie zastosowano klauzulę `where` do filtrowania z tablicy te ciągi mające określoną długość.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [where, klauzula](../../../language-reference/keywords/where-clause.md)
- [Instrukcje: dynamiczne określanie filtrów predykatu w czasie wykonywania](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Instrukcje: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Instrukcje: zapytanie o pliki o określonym atrybucie lub nazwie (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
