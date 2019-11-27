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
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="5ea5d-102">Instrukcje: zapytanie o znaki w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ea5d-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="5ea5d-103">Ponieważ Klasa <xref:System.String> implementuje ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>, każdy ciąg może być badany jako sekwencja znaków.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="5ea5d-104">Nie jest to jednak powszechne użycie LINQ.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="5ea5d-105">W przypadku złożonych operacji dopasowania do wzorca Użyj klasy <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>

## <a name="example"></a><span data-ttu-id="5ea5d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ea5d-106">Example</span></span>

<span data-ttu-id="5ea5d-107">Poniższy przykład wysyła zapytanie do ciągu, aby określić liczbę cyfr, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="5ea5d-108">Należy pamiętać, że zapytanie jest "ponownie używane" po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="5ea5d-109">Jest to możliwe, ponieważ samo zapytanie nie przechowuje żadnych rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-109">This is possible because the query itself does not store any actual results.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="5ea5d-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5ea5d-110">Compiling the Code</span></span>

<span data-ttu-id="5ea5d-111">Utwórz projekt aplikacji konsolowej VB.NET z instrukcją `Imports` dla przestrzeni nazw System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="5ea5d-111">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ea5d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ea5d-112">See also</span></span>

- [<span data-ttu-id="5ea5d-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ea5d-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="5ea5d-114">Jak połączyć zapytania LINQ z wyrażeniami regularnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ea5d-114">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)
