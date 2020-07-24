---
title: Filtrowanie danych (C#)
description: Filtrowanie, znane także jako zaznaczenie, ogranicza wyniki na podstawie warunku. Dowiedz się więcej na temat standardowych metod operatorów zapytań w LINQ w języku C#, które wykonują filtrowanie.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103923"
---
# <a name="filtering-data-c"></a>Filtrowanie danych (C#)
Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek. Jest on również znany jako wybór.  
  
 Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków. Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Lokalizacja|Wybiera wartości, które są oparte na funkcji predykatu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 W poniższym przykładzie zastosowano `where` klauzulę do filtrowania z tablicy te ciągi mające określoną długość.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md)
- [Klauzula where](../../../language-reference/keywords/where-clause.md)
- [Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Jak wykonać zapytanie o pliki o określonym atrybucie lub nazwie (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
