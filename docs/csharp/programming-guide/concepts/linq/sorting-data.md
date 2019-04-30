---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: bceb599d9e8eb3c51c07526b9ad22d3d4206efdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711947"
---
# <a name="sorting-data-c"></a>Sortowanie danych (C#)
Operacja sortowania Porządkuje elementy które sekwencji, w oparciu o jeden lub więcej atrybutów. Kryterium sortowania sortuje podstawowe elementy. Określając drugie kryterium sortowania, możesz sortować elementów w każdej grupie podstawowej sortowania.  
  
 Poniższa ilustracja przedstawia wyniki operacji sortowania alfabetycznego na sekwencję znaków: 
  
 ![Grafika przedstawiająca operacji sortowania alfabetycznego.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 Metody standardowego operatora zapytań, sortować dane, które są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Sortuje wartości w kolejności rosnącej.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Wykonuje dodatkowej sortowanie w kolejności rosnącej.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Wykonuje dodatkowej sortowanie w kolejności malejącej.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|zwrotny|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="primary-sort-examples"></a>Przykłady podstawowej sortowania  
  
#### <a name="primary-ascending-sort"></a>Sortowanie w kolejności rosnącej podstawowego  
 Poniższy przykład pokazuje sposób użycia `orderby` klauzuli w zapytaniu LINQ, aby posortować ciągi w tablicy przez długość ciągu, w kolejności rosnącej.  
  
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
  
#### <a name="primary-descending-sort"></a>Podstawowy Sortuj malejąco  
 Następny przykład pokazuje sposób użycia `orderby descending` klauzuli w zapytaniu LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.  
  
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
  
### <a name="secondary-sort-examples"></a>Sortowanie dodatkowe przykłady  
  
#### <a name="secondary-ascending-sort"></a>Sortowanie w kolejności rosnącej dodatkowej  
 Poniższy przykład pokazuje sposób użycia `orderby` klauzuli w zapytaniu programu LINQ do wykonywania podstawowych i pomocniczych sortowania ciągów w tablicy. Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.  
  
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
  
#### <a name="secondary-descending-sort"></a>Pomocniczy Sortuj malejąco  
 Następny przykład pokazuje sposób użycia `orderby descending` klauzuli w zapytaniu LINQ, aby wykonać podstawowy sortowania, w kolejności rosnącej kolejności i dodatkowej sortowania, w kolejności malejącej. Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu.  
  
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
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [orderby, klauzula](../../../../csharp/language-reference/keywords/orderby-clause.md)
- [Instrukcje: Kolejność wyników klauzuli Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
