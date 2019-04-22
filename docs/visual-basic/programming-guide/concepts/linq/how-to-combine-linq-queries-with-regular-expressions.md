---
title: 'Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: da693b682e9b44970f167c030f6803f8dc6d2d36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820376"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a><span data-ttu-id="42ca5-102">Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ca5-102">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>
<span data-ttu-id="42ca5-103">W tym przykładzie pokazano, jak używać <xref:System.Text.RegularExpressions.Regex> klasy w celu utworzenia wyrażenia regularnego do dopasowania bardziej złożone w ciągów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="42ca5-103">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="42ca5-104">Zapytania LINQ można łatwo filtrować dane według dokładnie pliki, które chcesz przeszukać z wyrażeniem regularnym i kształtów wyników.</span><span class="sxs-lookup"><span data-stu-id="42ca5-104">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42ca5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="42ca5-105">Example</span></span>  
  
```vb  
Class LinqRegExVB  
  
    Shared Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        ' Modify this path as necessary so that it accesses your Visual Studio folder.  
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.  
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"
  
        ' Take a snapshot of the file system.  
        Dim fileList As IEnumerable(Of System.IO.FileInfo) = GetFiles(startFolder)  
  
        ' Create a regular expression to find all things "Visual".  
        Dim searchTerm As System.Text.RegularExpressions.Regex =   
            New System.Text.RegularExpressions.Regex("Visual (Basic|C#|C\+\+|Studio)")  
  
        ' Search the contents of each .htm file.  
        ' Remove the where clause to find even more matches!  
        ' This query produces a list of files where a match  
        ' was found, and a list of the matches in that file.  
        ' Note: Explicit typing of "Match" in select clause.  
        ' This is required because MatchCollection is not a   
        ' generic IEnumerable collection.  
        Dim queryMatchingFiles = From afile In fileList  
                                Where afile.Extension = ".htm"  
                                Let fileText = System.IO.File.ReadAllText(afile.FullName)  
                                Let matches = searchTerm.Matches(fileText)  
                                Where (matches.Count > 0)  
                                Select Name = afile.FullName,  
                                       Matches = From match As System.Text.RegularExpressions.Match In matches  
                                                 Select match.Value  
  
        ' Execute the query.  
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")  
  
        For Each fileMatches In queryMatchingFiles  
            ' Trim the path a bit, then write   
            ' the file name in which a match was found.  
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)  
            Console.WriteLine(s)  
  
            ' For this file, write out all the matching strings  
            For Each match In fileMatches.Matches  
                Console.WriteLine("  " + match)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit")  
        Console.ReadKey()  
    End Sub  
  
    ' Function to retrieve a list of files. Note that this is a copy  
    ' of the file information.  
    Shared Function GetFiles(ByVal root As String) As IEnumerable(Of System.IO.FileInfo)  
        Return From file In My.Computer.FileSystem.GetFiles(  
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")   
               Select New System.IO.FileInfo(file)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="42ca5-106">Należy zauważyć, że możesz także zbadać <xref:System.Text.RegularExpressions.MatchCollection> obiektu, który jest zwracany przez `RegEx` wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42ca5-106">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="42ca5-107">W tym przykładzie wartość każdego dopasowania jest generowany w wynikach.</span><span class="sxs-lookup"><span data-stu-id="42ca5-107">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="42ca5-108">Jednak użytkownik może również używać programu LINQ do wykonywania wszystkich rodzajów filtrowanie, sortowanie i grupowanie w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="42ca5-108">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="42ca5-109">Ponieważ <xref:System.Text.RegularExpressions.MatchCollection> jest nieogólnego <xref:System.Collections.IEnumerable> kolekcji, trzeba jawnie określać typu zmiennej zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="42ca5-109">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42ca5-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="42ca5-110">Compiling the Code</span></span>  
 <span data-ttu-id="42ca5-111">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="42ca5-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ca5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42ca5-112">See also</span></span>

- [<span data-ttu-id="42ca5-113">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ca5-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="42ca5-114">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42ca5-114">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
