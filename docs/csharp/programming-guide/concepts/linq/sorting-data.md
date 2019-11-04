---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 78b263c384895b736b11cc524befa42b4a896380
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418188"
---
# <a name="sorting-data-c"></a>Sortowanie danych (C#)
Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub większej liczby atrybutów. Pierwsze kryterium sortowania wykonuje podstawowe sortowanie elementów. Określając drugie kryterium sortowania, można sortować elementy w ramach każdej podstawowej grupy sortowania.  
  
 Na poniższej ilustracji przedstawiono wyniki alfabetycznej operacji sortowania na sekwencji znaków: 
  
 ![Grafika pokazująca alfabetyczną operację sortowania.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Standardowe metody operatorów zapytań, które sortują dane, są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Sortuje wartości w kolejności rosnącej.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Wykonuje sortowanie pomocnicze w kolejności rosnącej.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Wykonuje sortowanie pomocnicze w kolejności malejącej.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Cofnięci|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="primary-sort-examples"></a>Główne przykłady sortowania  
  
#### <a name="primary-ascending-sort"></a>Podstawowe sortowanie rosnące  
 Poniższy przykład ilustruje sposób użycia klauzuli `orderby` w zapytaniu LINQ do sortowania ciągów w tablicy według długości ciągu w kolejności rosnącej.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a>Sortowanie sortowania podstawowego  
 W następnym przykładzie pokazano, jak używać klauzuli `orderby descending` w zapytaniu LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a>Przykłady sortowania pomocniczego  
  
#### <a name="secondary-ascending-sort"></a>Sortowanie pomocnicze rosnąco  
 W poniższym przykładzie pokazano, jak używać klauzuli `orderby` w zapytaniu LINQ, aby wykonać podstawowe i pomocnicze sortowanie ciągów w tablicy. Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu, zarówno w kolejności rosnącej.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a>Sortowanie malejąco  
 W następnym przykładzie pokazano, jak używać klauzuli `orderby descending` w zapytaniu LINQ do wykonywania sortowania podstawowego w kolejności rosnącej i sortowania pomocniczego w kolejności malejącej. Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [orderby, klauzula](../../../language-reference/keywords/orderby-clause.md)
- [Instrukcje: kolejność wyników klauzuli join](../../../linq/order-the-results-of-a-join-clause.md)
- [Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
