---
title: 'Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: 0b61b75c5f26c48d817b8f51c740cc1758607838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643198"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)
W tym przykładzie pokazano, jak można znaleźć w pliku tekstowym, która zawiera dopasowań dla każdego określony zestaw wyrazów zdań. Tablica terminy wyszukiwania ma ustalony w tym przykładzie, ale jego można również można wypełnić dynamicznie w czasie wykonywania. W tym przykładzie zapytanie zwraca zdania zawierające słowa "Historycznie", "dane" i "zintegrowane".  
  
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
  
 Zapytanie działa najpierw podziału tekstu do zdań, a następnie Podziel zdania na tablicę ciągów zawierających każdego wyrazu. Dla każdego z tych tablic <xref:System.Linq.Enumerable.Distinct%2A> metoda usuwa wszystkie zduplikowane słowa, a następnie wykonuje zapytanie <xref:System.Linq.Enumerable.Intersect%2A> operacji na tablicy programu word i `wordsToMatch` tablicy. Jeśli liczba przecięcie jest taka sama jak liczba `wordsToMatch` tablicy, nie znaleziono wszystkich wyrazów w wyrazy i zdanie oryginalna jest zwracana.  
  
 W wywołaniu <xref:System.String.Split%2A>, aby można było je usunąć z ciągu służą jako separatorów znaków interpunkcyjnych. Jeśli nie zrobisz, na przykład można używać ciągu "W przeszłości", który będzie niezgodny "W przeszłości" w `wordsToMatch` tablicy. Użytkownik może być konieczne użycie dodatkowych separatorów, w zależności od typów znaków interpunkcyjnych, zazwyczaj w tekstach źródła.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
