---
title: Sposób łączenia zapytań LINQ z wyrażeniami regularnymi
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: a091418be1f7cc30d42a98f80ebae2d36d29b5d8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337547"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a>Jak połączyć zapytania LINQ z wyrażeniami regularnymi (Visual Basic)

Ten przykład pokazuje, jak używać klasy <xref:System.Text.RegularExpressions.Regex> do tworzenia wyrażenia regularnego w celu uzyskania bardziej złożonych odpowiedników w ciągach tekstowych. Zapytanie LINQ ułatwia filtrowanie według dokładnie plików, które mają być przeszukiwane przy użyciu wyrażenia regularnego, oraz do kształtowania wyników.

## <a name="example"></a>Przykład

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
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
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

Należy zauważyć, że można także zbadać obiekt <xref:System.Text.RegularExpressions.MatchCollection>, który jest zwracany przez wyszukiwanie `RegEx`. W tym przykładzie tylko wartość każdego dopasowania jest generowana w wynikach. Można jednak używać LINQ do wykonywania wszelkiego rodzaju filtrowania, sortowania i grupowania w tej kolekcji. Ponieważ <xref:System.Text.RegularExpressions.MatchCollection> jest nieogólną kolekcją <xref:System.Collections.IEnumerable>, należy jawnie podać typ zmiennej zakresu w zapytaniu.

## <a name="compile-the-code"></a>Skompilować kod

Utwórz projekt aplikacji konsolowej Visual Basic, skopiuj i wklej przykładowy kod, a następnie Dostosuj wartość obiektu uruchomieniowego we właściwościach projektu.

## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (Visual Basic)](linq-and-strings.md)
- [LINQ i katalogi plików (Visual Basic)](linq-and-file-directories.md)
