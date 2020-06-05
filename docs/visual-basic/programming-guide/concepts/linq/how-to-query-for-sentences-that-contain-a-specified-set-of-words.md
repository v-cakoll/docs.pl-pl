---
title: 'Instrukcje: zapytanie o zdania zawierające określony zestaw słów (LINQ)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: ce88bf001346f90eb9b08ca1ff14afc7dcb04fa0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397963"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Instrukcje: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)

Ten przykład pokazuje, jak znaleźć zdania w pliku tekstowym zawierającym dopasowania dla każdego z określonych wyrazów. Mimo że tablica terminów wyszukiwania jest zakodowana w tym przykładzie, można ją również wypełnić dynamicznie w czasie wykonywania. W tym przykładzie zapytanie zwraca zdania zawierające słowa "historyczne", "dane" i "zintegrowane".

## <a name="example"></a>Przykład

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

Zapytanie działa przez pierwsze dzielenie tekstu na zdania, a następnie dzielenie zdań na tablicę ciągów, które zawierają każdy wyraz. Dla każdej z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> Metoda powoduje usunięcie wszystkich zduplikowanych wyrazów, a następnie zapytanie wykonuje <xref:System.Linq.Enumerable.Intersect%2A> operację na tablicy słów i `wordsToMatch` tablicy. Jeśli liczba przedziałów jest taka sama jak liczba `wordsToMatch` tablicy, wszystkie wyrazy zostały znalezione w wyrazach, a zdanie oryginalne zostanie zwrócone.

W wywołaniu do <xref:System.String.Split%2A> , znaki interpunkcyjne są używane jako separatory w celu usunięcia ich z ciągu. Jeśli tego nie zrobiono, na przykład możesz mieć ciąg "historyczny", który nie pasuje do "historycznie" w `wordsToMatch` tablicy. Może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych znalezionych w tekście źródłowym.

## <a name="compile-the-code"></a>Kompiluj kod

Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu `Imports` instrukcji dla przestrzeni nazw System. LINQ.

## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (Visual Basic)](linq-and-strings.md)
