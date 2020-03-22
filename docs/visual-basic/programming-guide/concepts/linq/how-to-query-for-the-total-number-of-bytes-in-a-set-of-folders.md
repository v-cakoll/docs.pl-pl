---
title: 'Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 25e2c2894d9feccf42ee92bdddd17d8558779e6c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266979"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Jak: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)
W tym przykładzie pokazano, jak pobrać całkowitą liczbę bajtów używanych przez wszystkie pliki w określonym folderze i wszystkie jego podfoldery.  
  
## <a name="example"></a>Przykład  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> dodaje wartości wszystkich elementów wybranych `select` w klauzuli. Tę kwerendę można łatwo zmodyfikować, aby pobrać największy lub najmniejszy plik <xref:System.Linq.Enumerable.Min%2A> w <xref:System.Linq.Enumerable.Max%2A> określonym drzewie katalogów, <xref:System.Linq.Enumerable.Sum%2A>wywołując metodę lub metodę zamiast .  
  
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
  
 Jeśli trzeba tylko policzyć liczbę bajtów w określonym drzewie katalogów, można to zrobić bardziej efektywnie bez tworzenia kwerendy LINQ, która ponosi obciążenie związane z tworzeniem kolekcji listy jako źródła danych. Przydatność metody LINQ zwiększa się, jak kwerenda staje się bardziej złożone lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.  
  
 Kwerenda wywołuje oddzielną metodę, aby uzyskać długość pliku. Robi to w celu wykorzystania możliwego wyjątku, który zostanie podniesiony, <xref:System.IO.FileInfo> jeśli plik został `GetFiles`usunięty w innym wątku po utworzeniu obiektu w wywołaniu . Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek <xref:System.IO.FileInfo> może wystąpić, <xref:System.IO.FileInfo.Length%2A> ponieważ obiekt spróbuje odświeżyć jego właściwość o najbardziej bieżącej długości przy pierwszym wejściu do właściwości. Umieszczając tę operację w bloku try-catch poza kwerendą, kod jest zgodny z regułą unikania operacji w kwerendach, które mogą powodować skutki uboczne. Ogólnie rzecz biorąc należy zwrócić szczególną uwagę podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compile-the-code"></a>Skompiluj kod  
Utwórz projekt aplikacji konsoli języka `Imports` Visual Basic z instrukcją dla obszaru nazw System.Linq.
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
