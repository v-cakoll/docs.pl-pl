---
title: 'Instrukcje: Liczba wystąpień wyrazu w ciągu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051744"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="fde40-102">Instrukcje: Liczba wystąpień wyrazu w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fde40-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="fde40-103">W tym przykładzie pokazano, jak korzystać z zapytania LINQ można zliczać wystąpienia określonego wyrazu w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fde40-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="fde40-104">Należy pamiętać, że przeprowadzenie liczba <xref:System.String.Split%2A> metoda jest wywoływana, aby utworzyć tablicę słów.</span><span class="sxs-lookup"><span data-stu-id="fde40-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="fde40-105">Występuje spadek wydajności, aby <xref:System.String.Split%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fde40-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="fde40-106">W przypadku operacji tylko na ciąg do zliczania wyrazów, należy rozważyć użycie <xref:System.Text.RegularExpressions.Regex.Matches%2A> lub <xref:System.String.IndexOf%2A> metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="fde40-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="fde40-107">Jednak jeśli wydajność nie jest to problem krytyczny lub ma już Podziel zdania w celu wykonywania innych typów kwerend nad nim, następnie dobrym pomysłem liczba słów lub fraz, a także przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="fde40-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fde40-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fde40-108">Example</span></span>  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fde40-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fde40-109">Compiling the Code</span></span>  
 <span data-ttu-id="fde40-110">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="fde40-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde40-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fde40-111">See also</span></span>

- [<span data-ttu-id="fde40-112">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fde40-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
