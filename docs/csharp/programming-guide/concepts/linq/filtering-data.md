---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: dc31a73a8ebbe52f7d22984cd747a038e2556c28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634639"
---
# <a name="filtering-data-c"></a>Filtrowanie danych (C#)
Filtrowanie odnosi się do operacji ograniczyć zestaw wyników, aby zawiera tylko te elementy, które spełniają określony warunek. Jest również nazywany zaznaczenia.  
  
 Poniższa ilustracja przedstawia wyniki filtrowania sekwencji znaków. Predykat dla filtrowania operacji określa, że znak musi być "A".  
  
 ![Filtrowanie operację LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 Metody standardowego operatora zapytań, które wykonują wyboru są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Wybiera wartości, w zależności od ich możliwości, można rzutować do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Gdzie|Wybiera wartości, które są oparte na funkcji predykatu.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 W poniższym przykładzie użyto `where` klauzulę filtrującą dane z tablicy tych ciągów, które mają określonej długości.  
  
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
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [where, klauzula](../../../../csharp/language-reference/keywords/where-clause.md)
- [Instrukcje: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Instrukcje: Zapytanie o pliki o określonym atrybucie lub nazwie (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
