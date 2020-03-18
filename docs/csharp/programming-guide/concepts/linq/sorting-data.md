---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167910"
---
# <a name="sorting-data-c"></a>Sortowanie danych (C#)
Operacja sortowania porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów. Pierwsze kryterium sortowania wykonuje sortowanie podstawowe na elementach. Określając drugie kryterium sortowania, można sortować elementy w każdej podstawowej grupie sortowania.  
  
 Na poniższej ilustracji przedstawiono wyniki operacji sortowania alfabetycznego na sekwencji znaków:
  
 ![Grafika przedstawiająca operację sortowania alfabetycznego.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Standardowe metody operatora kwerendy, które sortują dane są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Orderby|Sortuje wartości w porządku rosnącym.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|Orderbydescending|Sortuje wartości w kolejności malejącej.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|Thenby|Wykonuje sortowanie pomocnicze w kolejności rosnącej.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|Thenbydescending|Wykonuje sortowanie pomocnicze w kolejności malejącej.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażenia kwerendy  
  
### <a name="primary-sort-examples"></a>Podstawowe przykłady sortowania  
  
#### <a name="primary-ascending-sort"></a>Podstawowy sortowanie wstępne  
 W poniższym przykładzie pokazano, jak używać `orderby` klauzuli w kwerendzie LINQ do sortowania ciągów w tablicy według długości ciągu, w kolejności rosnącej.  
  
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
  
#### <a name="primary-descending-sort"></a>Podstawowy sortowanie malejące  
 W następnym przykładzie pokazano, `orderby descending` jak używać klauzuli w kwerendzie LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.  
  
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
  
#### <a name="secondary-ascending-sort"></a>Pomocniczy sortowanie wstępne  
 W poniższym przykładzie pokazano, jak używać `orderby` klauzuli w kwerendzie LINQ do wykonywania podstawowego i pomocniczego rodzaju ciągów w tablicy. Ciągi są sortowane głównie według długości i drugorzędnie według pierwszej litery ciągu, zarówno w porządku rosnącym.  
  
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
  
#### <a name="secondary-descending-sort"></a>Pomocniczy sortowanie malejące  
 W następnym przykładzie pokazano, `orderby descending` jak używać klauzuli w kwerendzie LINQ do wykonywania sortowania podstawowego, w porządku rosnącym i sortowania pomocniczego w kolejności malejącej. Ciągi są sortowane głównie według długości i drugorzędnie według pierwszej litery ciągu.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Klauzula orderby](../../../language-reference/keywords/orderby-clause.md)
- [Kolejność wyników klauzuli join](../../../linq/order-the-results-of-a-join-clause.md)
- [Jak sortować lub filtrować dane tekstowe według dowolnego wyrazu lub pola (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
