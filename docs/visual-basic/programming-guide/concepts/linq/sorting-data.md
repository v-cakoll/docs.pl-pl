---
title: Sortowanie danych
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406797"
---
# <a name="sorting-data-visual-basic"></a>Sortowanie danych (Visual Basic)

Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub większej liczby atrybutów. Pierwsze kryterium sortowania wykonuje podstawowe sortowanie elementów. Określając drugie kryterium sortowania, można sortować elementy w ramach każdej podstawowej grupy sortowania.

Na poniższej ilustracji przedstawiono wyniki alfabetycznej operacji sortowania na sekwencji znaków.

![Grafika pokazująca alfabetyczną operację sortowania.](./media/sorting-data/alphabetical-sort-operation.png)

Standardowe metody operatorów zapytań, które sortują dane, są wymienione w poniższej sekcji.

## <a name="methods"></a>Metody

|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|
|-----------------|-----------------|------------------------------------------|----------------------|
|OrderBy|Sortuje wartości w kolejności rosnącej.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|OrderByDescending|Sortuje wartości w kolejności malejącej.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|ThenBy|Wykonuje sortowanie pomocnicze w kolejności rosnącej.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|ThenByDescending|Wykonuje sortowanie pomocnicze w kolejności malejącej.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|Reverse|Odwraca kolejność elementów w kolekcji.|Nie dotyczy.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania

### <a name="primary-sort-examples"></a>Główne przykłady sortowania

#### <a name="primary-ascending-sort"></a>Podstawowe sortowanie rosnące

Poniższy przykład ilustruje sposób użycia `Order By` klauzuli w zapytaniu LINQ do sortowania ciągów w tablicy według długości ciągu w kolejności rosnącej.

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

#### <a name="primary-descending-sort"></a>Sortowanie sortowania podstawowego

W następnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytaniu LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.

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

### <a name="secondary-sort-examples"></a>Przykłady sortowania pomocniczego

#### <a name="secondary-ascending-sort"></a>Sortowanie pomocnicze rosnąco

Poniższy przykład ilustruje sposób użycia `Order By` klauzuli w zapytaniu LINQ do wykonywania podstawowego i pomocniczego sortowania ciągów w tablicy. Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu, zarówno w kolejności rosnącej.

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

#### <a name="secondary-descending-sort"></a>Sortowanie malejąco

W następnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytaniu LINQ do wykonywania sortowania podstawowego w kolejności rosnącej i sortowania pomocniczego w kolejności malejącej. Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu.

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

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Order By, klauzula](../../../language-reference/queries/order-by-clause.md)
- [Instrukcje: sortowanie wyników zapytania](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
