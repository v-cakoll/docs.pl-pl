---
title: 'Porady: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 7a8314ba6109f25b4bc5f5952b358695844eadab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="6570f-102">Porady: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6570f-102">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>
<span data-ttu-id="6570f-103">W tym przykładzie pokazano, jak można odnaleźć wszystkich plików mających rozszerzenie nazwy pliku (na przykład "txt") w drzewie określonego katalogu.</span><span class="sxs-lookup"><span data-stu-id="6570f-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="6570f-104">Ponadto sposób zwracania albo pliku najnowsze lub najstarsze w drzewie na podstawie czasu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="6570f-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6570f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6570f-105">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6570f-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6570f-106">Compiling the Code</span></span>  
 <span data-ttu-id="6570f-107">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6570f-107">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6570f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6570f-108">See Also</span></span>  
 [<span data-ttu-id="6570f-109">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6570f-109">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="6570f-110">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6570f-110">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
