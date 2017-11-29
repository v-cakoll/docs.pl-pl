---
title: "Porady: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e2d81f88371e63f64567422e87ed5b185e7a633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="d1232-102">Porady: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1232-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="d1232-103">Ten przykład przedstawia, jak LINQ może służyć do wykonywania zaawansowanych grupowanie i sortowanie operacje na listach plików lub folderów.</span><span class="sxs-lookup"><span data-stu-id="d1232-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="d1232-104">Przedstawiono również sposób strony danych wyjściowych w oknie konsoli przy użyciu <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d1232-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1232-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1232-105">Example</span></span>  
 <span data-ttu-id="d1232-106">Następujące zapytanie Wyświetla sposób grupowania zawartość drzewa katalogów określonego przez rozszerzenie nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d1232-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of   
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console diplay for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to diplay  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d1232-107">Dane wyjściowe z tego programu może trwać długo, zależnie od szczegóły lokalnego systemu plików i `startFolder` ma ustawioną wartość.</span><span class="sxs-lookup"><span data-stu-id="d1232-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="d1232-108">Aby umożliwić wyświetlanie wszystkich wyników, w tym przykładzie przedstawiono sposób przeglądania wyników.</span><span class="sxs-lookup"><span data-stu-id="d1232-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="d1232-109">Te same techniki może odnosić się do systemu Windows i aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d1232-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="d1232-110">Należy zauważyć, że ponieważ kod strony elementów w grupie, zagnieżdżone `For Each` pętli jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d1232-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="d1232-111">Istnieje również dodatkową logikę do obliczenia bieżącej pozycji na liście i aby umożliwić użytkownikowi Zatrzymaj stronicowania, a następnie zamknij program.</span><span class="sxs-lookup"><span data-stu-id="d1232-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="d1232-112">W tym przypadku stronicowania zapytanie jest wykonywane na buforowanych wyników z oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="d1232-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="d1232-113">W innych kontekstach, takich jak LINQ do SQL takich buforowanie nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d1232-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1232-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d1232-114">Compiling the Code</span></span>  
 <span data-ttu-id="d1232-115">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d1232-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1232-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1232-116">See Also</span></span>  
 [<span data-ttu-id="d1232-117">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1232-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="d1232-118">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1232-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
