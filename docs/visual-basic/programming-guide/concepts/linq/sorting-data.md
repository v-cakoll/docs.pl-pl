---
title: Sortowanie danych (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a>Sortowanie danych (Visual Basic)
Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów. Pierwsze kryterium sortowania sortuje podstawowe elementy. Określając drugie kryterium sortowania, można sortować elementów w każdej grupie głównej sortowania.  
  
 Na poniższej ilustracji przedstawiono wyniki operacji alfabetycznej sortowania na sekwencję znaków.  
  
 ![Operacja sortowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Metody operator standardowej kwerendy, które sortować dane są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OrderBy|Sortuje wartości w kolejności rosnącej.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|Wykonuje dodatkowej sortowania w porządku rosnącym.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|Sortuje dodatkowej w kolejności malejącej.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="primary-sort-examples"></a>Przykłady głównej sortowania  
  
#### <a name="primary-ascending-sort"></a>Podstawowy sortowanie w kolejności rosnącej  
 W poniższym przykładzie pokazano sposób użycia `Order By` klauzuli w kwerendzie LINQ, aby posortować ciągów w tablicy, długość ciągu w kolejności rosnącej.  
  
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
  
#### <a name="primary-descending-sort"></a>Podstawowy malejącym  
 Kolejnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytania LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.  
  
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
  
### <a name="secondary-sort-examples"></a>Przykłady sortowania  
  
#### <a name="secondary-ascending-sort"></a>Sortowanie w kolejności rosnącej dodatkowej  
 W poniższym przykładzie pokazano sposób użycia `Order By` podklauzul LINQ do wykonywania podstawowych i pomocniczych sortowanie ciągów w tablicy. Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.  
  
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
  
#### <a name="secondary-descending-sort"></a>Dodatkowej malejącym  
 Kolejnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytania LINQ, aby wykonać podstawowy sortowania, w rosnącej kolejności i drugiego sortowania w kolejności malejącej. Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Order By — klauzula](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Porady: sortowanie wyników zapytania](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
