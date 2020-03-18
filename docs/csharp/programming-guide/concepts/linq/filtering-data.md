---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346993"
---
# <a name="filtering-data-c"></a>Filtrowanie danych (C#)
Filtrowanie odnosi się do działania ograniczajączestaw wyników zawierać tylko te elementy, które spełniają określony warunek. Jest również znany jako wybór.  
  
 Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków. Predykat dla operacji filtrowania określa, że znak musi być "A".  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Standardowe metody operatora kwerendy, które wykonują wybór są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Oftype|Wybiera wartości, w zależności od ich zdolności do rzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Lokalizacja|Wybiera wartości, które są oparte na funkcji predykatu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia kwerendy  
 W poniższym `where` przykładzie użyto klauzuli do filtrowania z tablicy tych ciągów, które mają określoną długość.  
  
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
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [gdzie klauzula](../../../language-reference/keywords/where-clause.md)
- [Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Jak wysyłać zapytania do metadanych zestawu za pomocą odbicia (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Jak wysyłać zapytania do plików o określonym atrybucie lub nazwie (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Jak sortować lub filtrować dane tekstowe według dowolnego wyrazu lub pola (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
