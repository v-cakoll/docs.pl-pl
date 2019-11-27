---
title: 'Porady: zapytanie o znaki w ciągu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 9da6d5abd6155a7af5ec59e17693e8acae7e7b73
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347721"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Instrukcje: zapytanie o znaki w ciągu (LINQ) (Visual Basic)

Ponieważ Klasa <xref:System.String> implementuje ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>, każdy ciąg może być badany jako sekwencja znaków. Nie jest to jednak powszechne użycie LINQ. W przypadku złożonych operacji dopasowania do wzorca Użyj klasy <xref:System.Text.RegularExpressions.Regex>.

## <a name="example"></a>Przykład

Poniższy przykład wysyła zapytanie do ciągu, aby określić liczbę cyfr, które zawiera. Należy pamiętać, że zapytanie jest "ponownie używane" po raz pierwszy. Jest to możliwe, ponieważ samo zapytanie nie przechowuje żadnych rzeczywistych wyników.

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Utwórz projekt aplikacji konsolowej VB.NET z instrukcją `Imports` dla przestrzeni nazw System. LINQ.

## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (Visual Basic)](linq-and-strings.md)
- [Jak połączyć zapytania LINQ z wyrażeniami regularnymi (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)
