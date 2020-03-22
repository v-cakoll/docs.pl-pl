---
title: 'Porady: grupowanie plików według rozszerzenia (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 4d2c51fa62b3ec144bc5ad51b4a9f8305476645e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267031"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>Jak: Grupowanie plików według rozszerzenia (LINQ) (Visual Basic)
W tym przykładzie pokazano, jak LINQ może służyć do wykonywania zaawansowanych operacji grupowania i sortowania na listach plików lub folderów. Pokazuje również, jak strona danych wyjściowych <xref:System.Linq.Enumerable.Skip%2A> w <xref:System.Linq.Enumerable.Take%2A> oknie konsoli przy użyciu i metody.  
  
## <a name="example"></a>Przykład  
 W poniższej kwerendzie pokazano, jak grupować zawartość określonego drzewa katalogów przez rozszerzenie nazwy pliku.  
  
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
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
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
  
 Dane wyjściowe z tego programu mogą być długie, w zależności `startFolder` od szczegółów lokalnego systemu plików i tego, na co jest ustawione. Aby włączyć wyświetlanie wszystkich wyników, w tym przykładzie pokazano, jak strony za pośrednictwem wyników. Te same techniki można zastosować do systemu Windows i aplikacji sieci Web. Należy zauważyć, że ponieważ strony kodowe elementy `For Each` w grupie, zagnieżdżona pętla jest wymagana. Istnieje również kilka dodatkowych logiki obliczania bieżącej pozycji na liście i aby umożliwić użytkownikowi zatrzymanie stronicowania i wyjście z programu. W tym konkretnym przypadku kwerenda stronicowania jest uruchamiana względem buforowanych wyników z oryginalnej kwerendy. W innych kontekstach, takich jak LINQ do SQL, takie buforowanie nie jest wymagane.  
  
## <a name="compile-the-code"></a>Skompiluj kod  
Utwórz projekt aplikacji konsoli języka `Imports` Visual Basic z instrukcją dla obszaru nazw System.Linq.
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
