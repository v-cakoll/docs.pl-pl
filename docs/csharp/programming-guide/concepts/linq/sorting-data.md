---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 6e223ecbfc68e904762bff998b3bd37f88607f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332562"
---
# <a name="sorting-data-c"></a>Sortowanie danych (C#)
Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów. Pierwsze kryterium sortowania sortuje podstawowe elementy. Określając drugie kryterium sortowania, można sortować elementów w każdej grupie głównej sortowania.  
  
 Na poniższej ilustracji przedstawiono wyniki operacji alfabetycznej sortowania na sekwencję znaków.  
  
 ![Operacja sortowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Metody operator standardowej kwerendy, które sortować dane są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|Sortuje wartości w kolejności rosnącej.|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Wykonuje dodatkowej sortowania w porządku rosnącym.|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Sortuje dodatkowej w kolejności malejącej.|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="primary-sort-examples"></a>Przykłady głównej sortowania  
  
#### <a name="primary-ascending-sort"></a>Podstawowy sortowanie w kolejności rosnącej  
 W poniższym przykładzie pokazano sposób użycia `orderby` klauzuli w kwerendzie LINQ, aby posortować ciągów w tablicy, długość ciągu w kolejności rosnącej.  
  
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
  
#### <a name="primary-descending-sort"></a>Podstawowy malejącym  
 Kolejnym przykładzie pokazano, jak używać `orderby``descending` klauzuli w zapytania LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.  
  
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
  
### <a name="secondary-sort-examples"></a>Przykłady sortowania  
  
#### <a name="secondary-ascending-sort"></a>Sortowanie w kolejności rosnącej dodatkowej  
 W poniższym przykładzie pokazano sposób użycia `orderby` podklauzul LINQ do wykonywania podstawowych i pomocniczych sortowanie ciągów w tablicy. Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.  
  
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
  
#### <a name="secondary-descending-sort"></a>Dodatkowej malejącym  
 Kolejnym przykładzie pokazano, jak używać `orderby``descending` klauzuli w zapytania LINQ, aby wykonać podstawowy sortowania, w rosnącej kolejności i drugiego sortowania w kolejności malejącej. Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu.  
  
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
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [orderby, klauzula](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [Porady: kolejność wyników klauzuli Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
