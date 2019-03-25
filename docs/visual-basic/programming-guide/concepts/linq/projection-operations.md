---
title: Operacje rzutowania (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: f7f1ba7b595d5ea63468aaa2d4fdda62cb9d0693
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408954"
---
# <a name="projection-operations-visual-basic"></a>Operacje rzutowania (Visual Basic)
Projekcja odnosi się do operacji przekształcania obiektu w nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte. Korzystając z funkcji projekcji, możesz utworzyć nowy typ, który jest zbudowany z każdego obiektu. Można właściwość projektu i wykonywać w niej funkcji matematycznych. Można również projektu oryginalnego obiektu, nie zmieniając go.  
  
 Metody standardowego operatora zapytań, które wykonują rzutowania są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Wybierz|Wartości projektów, które są oparte na funkcji przekształcenia.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projekty sekwencje wartości, które są oparte na funkcji przekształcenia i spłaszcza je do jednej sekwencji.|Używanych jest wiele `From` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="select"></a>Wybierz  
 W poniższym przykładzie użyto `Select` klauzuli do projektu pierwszą literę każdego ciągu w postaci listy ciągów.  
  
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
 W poniższym przykładzie użyto wielu `From` klauzul do projektu każdy wyraz z każdego ciągu w postaci listy ciągów.  
  
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
 Pracę obu `Select()` i `SelectMany()` jest do tworzenia wartości wyniku (lub wartości) z wartości źródłowe. `Select()` Tworzy jednej wartości wyniku dla każdej wartości źródła. Ogólny wynik jest w związku z tym kolekcji, który ma taką samą liczbę elementów jako kolekcja źródłowa. Z kolei `SelectMany()` tworzy jeden wynik ogólny, który zawiera połączonych podkolekcji od każdej wartości źródła. Funkcja transformacji, który jest przekazywany jako argument do `SelectMany()` musi zwracać wyliczalny sekwencję wartości dla każdej wartości źródła. Te sekwencje wyliczalny są następnie łączone przez `SelectMany()` do utworzenia jednej sekwencji dużych.  
  
 Na poniższych ilustracjach dwóch przedstawiono koncepcyjny różnica między akcje te dwie metody. W każdym przypadku założono, że funkcja selektor (przekształcenia) wybiera tablicy kwiatów od każdej wartości źródła.  
  
 Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcja źródłowa.  
  
 ![Grafika przedstawiająca akcji Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Ta ilustracja przedstawia sposób `SelectMany()` łączy pośrednich sekwencję tablic w jedną wartość na wynik końcowy zawierający wartość każdej z każdej macierzy pośrednich.  
  
 ![Grafika przedstawiająca akcji SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie porównano zachowanie `Select()` i `SelectMany()`. Ten kod tworzy "bouquet" kwiatów, pobierając dwóch pierwszych elementów z każdego listę nazw Kwiatek w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość", funkcja transformacji <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości. Ta migracja wymaga nadmiarowe `For Each` pętli, aby można było wyliczyć każdego ciągu w każdej podrzędnej sekwencji.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Select, klauzula](../../../../visual-basic/language-reference/queries/select-clause.md)
- [Instrukcje: Łączenie danych za pomocą sprzężeń](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Instrukcje: Zwracanie wyniku zapytania LINQ jako określonego typu](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
