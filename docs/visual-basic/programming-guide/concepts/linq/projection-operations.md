---
title: Operacje rzutowania
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 4795bdaba53949b34fe380ea9c51025ce43c40db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396340"
---
# <a name="projection-operations-visual-basic"></a>Operacje projekcji (Visual Basic)

Projekcja odnosi się do operacji przekształcenia obiektu w nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte. Korzystając z projekcji, można utworzyć nowy typ, który jest zbudowany z każdego obiektu. Można projektować Właściwość i wykonywać na niej funkcję matematyczną. Możesz również projektować oryginalny obiekt bez zmieniania go.

W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują projekcję.

## <a name="methods"></a>Metody

|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|
|-----------------|-----------------|------------------------------------------|----------------------|
|Wybierz pozycję|Project wartości, które są oparte na funkcji transformacji.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|SelectMany|Projektuje sekwencje wartości, które są oparte na funkcji transformacji, a następnie spłaszcza je w jedną sekwencję.|Używanie wielu `From` klauzul|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania

### <a name="select"></a>Wybierz pozycję

W poniższym przykładzie zastosowano `Select` klauzulę, aby zaprojektować pierwszą literę z każdego ciągu na liście ciągów.

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a>SelectMany

Poniższy przykład używa wielu `From` klauzul do tworzenia projektów każdego wyrazu z każdego ciągu na liście ciągów.

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a>Wybierz i SelectMany

Prace obu `Select()` i `SelectMany()` to generowanie wartości wyniku (lub wartości) z wartości źródłowych. `Select()`tworzy jedną wartość wynikową dla każdej wartości źródłowej. Ogólny wynik to kolekcja, która ma taką samą liczbę elementów jak kolekcja źródłowa. Z kolei program `SelectMany()` tworzy pojedynczy wynik ogólny, który zawiera połączone podkolekcje z każdej wartości źródłowej. Funkcja Transform, która jest przenoszona jako argument do `SelectMany()` musi zwracać wyliczalną sekwencję wartości dla każdej wartości źródłowej. Te wyliczalne sekwencje są następnie łączone przez program, `SelectMany()` Aby utworzyć jedną dużą sekwencję.

Poniższe dwa ilustracje pokazują różnicę koncepcyjną między działaniami tych dwóch metod. W każdym przypadku Załóżmy, że funkcja selektor (Transform) wybiera tablicę kwiatów z każdej wartości źródłowej.

Na tej ilustracji przedstawiono sposób, w jaki `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jak kolekcja źródłowa.

![Ilustracja przedstawiająca akcję wyboru&#40;&#41;](./media/projection-operations/select-action-graphic.png)

Na tej ilustracji przedstawiono sposób `SelectMany()` łączenia pośredniej sekwencji tablic w jedną końcową wartość wynikową, która zawiera każdą wartość z każdej tablicy pośredniej.

![Ilustracja przedstawiająca akcję SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a>Przykład kodu

Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()` . Kod tworzy "bukiet" kwiatów, pobierając pierwsze dwa elementy z każdej listy nazw kwiatów w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość", która jest wykorzystywana przez funkcję transformacji, <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> jest sama kolekcją wartości. Wymaga to dodatkowej `For Each` pętli, aby wyliczyć każdy ciąg w każdej sekwencji podrzędnej.

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [SELECT — klauzula](../../../language-reference/queries/select-clause.md)
- [Instrukcje: łączenie danych z sprzężeniami](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Instrukcje: wypełnianie kolekcji obiektów z wielu źródeł (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Instrukcje: zwracanie wyniku zapytania LINQ jako określonego typu](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Instrukcje: dzielenie pliku na wiele plików przy użyciu grup (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
