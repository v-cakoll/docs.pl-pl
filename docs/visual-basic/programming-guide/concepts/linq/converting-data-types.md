---
title: Konwertowanie typów danych
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410854"
---
# <a name="converting-data-types-visual-basic"></a>Konwertowanie typów danych (Visual Basic)

Metody konwersji zmieniają typ obiektów wejściowych.

 Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach. Poniżej przedstawiono kilka przykładów:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metoda może służyć do włączenia kolekcji niesparametryzowanej dla zapytań LINQ.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> i <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> mogą być używane do wymuszenia natychmiastowego wykonania zapytania zamiast odliczenia go do momentu wyliczenia zapytania.

## <a name="methods"></a>Metody

W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.

Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane. Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.

|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|
|-----------------|-----------------|------------------------------------------|----------------------|
|AsEnumerable|Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601> .|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (rodzajowy) <xref:System.Linq.IQueryable> .|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Rzutowanie|Rzutuje elementy kolekcji na określony typ.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray —|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> oparciu o funkcję selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList —|Konwertuje kolekcję na <xref:System.Collections.Generic.List%601> . Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) w oparciu o funkcję selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania

Poniższy przykład kodu używa `From As` klauzuli do rzutowania typu na podtyp przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko dla podtypu.

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Klauzula from](../../../language-reference/queries/from-clause.md)
- [Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)
