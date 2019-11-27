---
title: Jak zbadać zawartość plików w folderze (LINQ)
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 02ffa398c495ca5af77685d62299c59cfc3b9d9c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347610"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="7d608-102">Jak zbadać zawartość plików w folderze (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d608-102">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7d608-103">Ten przykład pokazuje, jak badać wszystkie pliki w określonym drzewie katalogów, otwierać każdy plik i sprawdzać jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="7d608-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="7d608-104">Ten typ technika może służyć do tworzenia indeksów lub odwracania indeksów zawartości drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="7d608-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="7d608-105">W tym przykładzie jest wykonywane proste wyszukiwanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="7d608-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="7d608-106">Jednak bardziej złożone typy dopasowywania do wzorców można wykonać przy użyciu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="7d608-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="7d608-107">Aby uzyskać więcej informacji, zobacz [How to: łączenie LINQ zapytań z wyrażeniami regularnymi (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7d608-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d608-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d608-108">Example</span></span>  
  
```vb
Imports System.IO

Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "C:\Program Files (x86)\Microsoft Visual Studio 14.0"  

        ' Take a snapshot of the folder contents.
        Dim dir As New DirectoryInfo(startFolder)
        Dim fileList = dir.GetFiles("*.*", SearchOption.AllDirectories)

        Dim searchTerm = "Welcome"

        ' Search the contents of each file.
        ' A regular expression created with the RegEx class
        ' could be used instead of the Contains method.
        Dim queryMatchingFiles = From file In fileList _
                                 Where file.Extension = ".html" _
                                 Let fileText = GetFileText(file.FullName) _
                                 Where fileText.Contains(searchTerm) _
                                 Select file.FullName

        Console.WriteLine("The term " & searchTerm & " was found in:")

        ' Execute the query.
        For Each filename In queryMatchingFiles
            Console.WriteLine(filename)
        Next

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()

    End Sub

    ' Read the contents of the file. This is done in a separate
    ' function in order to handle potential file system errors.
    Function GetFileText(name As String) As String

        ' If the file has been deleted, the right thing
        ' to do in this case is return an empty string.
        Dim fileContents = String.Empty

        ' If the file has been deleted since we took
        ' the snapshot, ignore it and return the empty string.
        If File.Exists(name) Then
            fileContents = File.ReadAllText(name)
        End If

        Return fileContents

    End Function
End Module
```

## <a name="compiling-the-code"></a><span data-ttu-id="7d608-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7d608-109">Compiling the code</span></span>

<span data-ttu-id="7d608-110">Utwórz projekt aplikacji konsolowej VB.NET, skopiuj i wklej przykładowy kod, a następnie Dostosuj wartość obiektu uruchomieniowego we właściwościach projektu.</span><span class="sxs-lookup"><span data-stu-id="7d608-110">Create a VB.NET console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d608-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d608-111">See also</span></span>

- [<span data-ttu-id="7d608-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d608-112">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="7d608-113">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d608-113">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
