---
title: 'Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 5eedd2ed0d8756f400f1ccfa1b1d71f699a42116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506605"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)
Ten przykład przedstawia sposób pobierania całkowita liczba bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.  
  
## <a name="example"></a>Przykład  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda dodaje wartość wszystkie aby elementy wybierane w `select` klauzuli. Można łatwo modyfikować to zapytanie, aby pobrać plik największą lub najmniejszą w drzewie katalogu określonego przez wywołanie metody <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast metody <xref:System.Linq.Enumerable.Sum%2A>.  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Jeśli masz tylko liczbę bajtów w drzewie określonego katalogu, możesz to zrobić w wydajniej bez tworzenia zapytania LINQ, którą jest naliczana kłopotów z tworzeniem kolekcji list jako źródła danych. Użyteczność podejście LINQ zwiększa zapytanie staje się bardziej złożone, lub gdy w celu uruchomienia wielu zapytań tego samego źródła danych.  
  
 Wywołuje zapytanie do oddzielnych metodach uzyskać długość pliku. Dzieje się tak aby można było korzystać z możliwych wyjątek, który zostanie wygenerowany, jeśli plik został usunięty w innym wątku po <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości o długości najbardziej aktualne po raz pierwszy uzyskano dostęp do właściwości. Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, kod poniżej reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne. Ogólnie rzecz biorąc doskonałe należy uważać, gdy wykorzystasz wyjątki, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.  
  
## <a name="see-also"></a>Zobacz także
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
