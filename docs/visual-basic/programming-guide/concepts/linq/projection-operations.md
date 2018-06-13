---
title: Operacje rzutowania (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: f4d1f7531ee69ebdbfb4ccd283f9f5dcb2f000af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647647"
---
# <a name="projection-operations-visual-basic"></a>Operacje rzutowania (Visual Basic)
Projekcja odwołuje się do operacji przekształcania obiektu na nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte. Przy użyciu projekcji, można utworzyć nowy typ, który składa się z każdego obiektu. Możesz właściwości projektu i funkcji matematycznych w nim. Można także wyświetlać oryginalny obiekt, bez jego zmiany.  
  
 Metody — operator zapytań standardowe, wykonujących projekcji są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Wybierz|Wartości projektów, które są oparte na funkcji przekształcenia.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Operacja SelectMany|Projekty sekwencji wartości, które są oparte na funkcji przekształcenia i spłaszcza je w jedną sekwencję.|Używanych jest wiele `From` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="select"></a>Wybierz  
 W poniższym przykładzie użyto `Select` klauzuli do projektu pierwszą literę każdego ciągu na liście ciągów.  
  
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
  
### <a name="selectmany"></a>Operacja SelectMany  
 W poniższym przykładzie użyto wielu `From` klauzule projektu każdego wyrazu z każdym ciągu na liście ciągów.  
  
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
  
## <a name="select-versus-selectmany"></a>Wybierz, a operacja SelectMany  
 Praca obu `Select()` i `SelectMany()` ma wartość wyniku (lub wartości) z wartości źródła. `Select()` tworzy jedną wartość wyniku dla każdej wartości źródła. Wynik ogólny w związku z tym jest kolekcja, która ma taką samą liczbę elementów jako kolekcji źródłowej. Z kolei `SelectMany()` tworzy jeden wynik ogólny zawierający połączonych podkolekcji od każdej wartości źródła. Przekazywany jako argument do funkcji przekształcenia `SelectMany()` musi zwracać wyliczalny sekwencji wartości dla każdej wartości źródła. Te wyliczalny sekwencje są następnie połączonych przez `SelectMany()` można utworzyć jedną dużą sekwencji.  
  
 Na poniższych ilustracjach dwóch przedstawiono koncepcyjnej różnica między działaniami te dwie metody. W każdym przypadku założono, że funkcja selektora (transform) wybiera tablicy kwiatów z każdej wartości źródła.  
  
 Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcji źródłowej.  
  
 ![Ilustracja akcji wybierz&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Ta ilustracja przedstawia sposób `SelectMany()` łączy pośredniego sekwencji tablic w jedną wartość wynik końcowy zawierający wartość każdej z poszczególnych pośrednia tablicy.  
  
 ![Grafika przedstawiająca akcji operacja SelectMany&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operacja SelectMany")  
  
### <a name="code-example"></a>Przykład kodu  
 Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()`. Kod tworzy "bouquet" kwiatów, wykonując dwóch pierwszych elementów z każdej listy nazw kwiat w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość" który funkcji przekształcenia <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości. Wymaga to nadmiarowe `For Each` pętli, aby można było wyliczyć każdy ciąg w każdej podrzędnej sekwencji.  
  
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
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Select, klauzula](../../../../visual-basic/language-reference/queries/select-clause.md)  
 [Porady: łączenie danych za pomocą sprzężeń](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
 [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Instrukcje: zwracanie wyniku zapytania LINQ jako określonego typu](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)  
 [Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
