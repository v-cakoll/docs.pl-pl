---
title: Filtrowanie danych
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 81e207e451055fb2952e4bf393db067f0851afb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353495"
---
# <a name="filtering-data-visual-basic"></a>Filtrowanie danych (Visual Basic)

Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek. Jest on również znany jako wybór.

Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków. Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".

![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)

W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.

## <a name="methods"></a>Metody

|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|
|-----------------|-----------------|------------------------------------------|----------------------|
|OfType|Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Gdzie|Wybiera wartości, które są oparte na funkcji predykatu.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania

Poniższy przykład używa `Where` do filtrowania z tablicy te ciągi mające określoną długość.

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Where, klauzula](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Instrukcje: filtrowanie wyników zapytania](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [Instrukcje: wykonywanie zapytania dotyczącego metadanych zestawu przy użyciu odbicia (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Instrukcje: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
