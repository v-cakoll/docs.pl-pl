---
title: 'Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c6490c8863b5762b0b487c6f3f3b2809e16d6519
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397937"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)
Ten przykład pokazuje, jak pobrać łączną liczbę bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.  
  
## <a name="example"></a>Przykład  
 <xref:System.Linq.Enumerable.Sum%2A>Metoda dodaje wartości wszystkich elementów wybranych w `select` klauzuli. Możesz łatwo zmodyfikować to zapytanie, aby pobrać największy lub najmniejszy plik w określonym drzewie katalogów, wywołując <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> metodę or zamiast <xref:System.Linq.Enumerable.Sum%2A> .  
  
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
  
 Jeśli musisz tylko policzyć liczbę bajtów w określonym drzewie katalogów, możesz to zrobić bardziej wydajnie bez tworzenia zapytania LINQ, które wiąże się z obciążeniem tworzenia kolekcji list jako źródła danych. Użyteczność podejścia LINQ zwiększa się, gdy zapytanie jest bardziej złożone, lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.  
  
 Zapytanie wywołuje oddzielną metodę w celu uzyskania długości pliku. Wykonuje to w celu użycia możliwego wyjątku, który zostanie wywołany, jeśli plik został usunięty z innego wątku po <xref:System.IO.FileInfo> utworzeniu obiektu w wywołaniu `GetFiles` . Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek może wystąpić, ponieważ <xref:System.IO.FileInfo> obiekt podejmie próbę odświeżenia swojej <xref:System.IO.FileInfo.Length%2A> właściwości z największą bieżącą długością dostępną do właściwości. Przez umieszczenie tej operacji w bloku try-catch poza zapytania, kod jest zgodny z regułą unikania operacji w zapytaniach, które mogą spowodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compile-the-code"></a>Kompiluj kod  
Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu `Imports` instrukcji dla przestrzeni nazw System. LINQ.
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](linq-and-file-directories.md)
