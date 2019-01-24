---
title: Sortowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: e36ccc72689e756105f51c988d4cafd06d4d8da5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520129"
---
# <a name="sorting-data-visual-basic"></a>Sortowanie danych (Visual Basic)
Operacja sortowania Porządkuje elementy które sekwencji, w oparciu o jeden lub więcej atrybutów. Kryterium sortowania sortuje podstawowe elementy. Określając drugie kryterium sortowania, możesz sortować elementów w każdej grupie podstawowej sortowania.  
  
 Poniższa ilustracja przedstawia wyniki operacji sortowania alfabetycznego na sekwencję znaków.  
  
 ![Sortowanie operację LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Metody standardowego operatora zapytań, sortować dane, które są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OrderBy|Sortuje wartości w kolejności rosnącej.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Wykonuje dodatkowej sortowanie w kolejności rosnącej.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Wykonuje dodatkowej sortowanie w kolejności malejącej.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|zwrotny|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="primary-sort-examples"></a>Przykłady podstawowej sortowania  
  
#### <a name="primary-ascending-sort"></a>Sortowanie w kolejności rosnącej podstawowego  
 Poniższy przykład pokazuje sposób użycia `Order By` klauzuli w zapytaniu LINQ, aby posortować ciągi w tablicy przez długość ciągu, w kolejności rosnącej.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a>Podstawowy Sortuj malejąco  
 Następny przykład pokazuje sposób użycia `Order By Descending` klauzuli w zapytaniu LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a>Sortowanie dodatkowe przykłady  
  
#### <a name="secondary-ascending-sort"></a>Sortowanie w kolejności rosnącej dodatkowej  
 Poniższy przykład pokazuje sposób użycia `Order By` klauzuli w zapytaniu programu LINQ do wykonywania podstawowych i pomocniczych sortowania ciągów w tablicy. Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a>Pomocniczy Sortuj malejąco  
 Następny przykład pokazuje sposób użycia `Order By Descending` klauzuli w zapytaniu LINQ, aby wykonać podstawowy sortowania, w kolejności rosnącej kolejności i dodatkowej sortowania, w kolejności malejącej. Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Order By, klauzula](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Instrukcje: Sortowanie wyników zapytania](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
