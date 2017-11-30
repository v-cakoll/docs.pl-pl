---
title: "Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b200581f4876400727c63e86e3ccf4a44c67914b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)
W tym przykładzie pokazano, jak pobrać całkowita liczba bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.  
  
## <a name="example"></a>Przykład  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda dodaje wartości wszystkich elementów wybranych w `select` klauzuli. Można łatwo zmodyfikować tego zapytania w celu pobrania plików największych lub najmniejszą w drzewie katalogu określonego przez wywołanie metody <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast metody <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Jeśli masz tylko liczbę bajtów w drzewie określonego katalogu, można w tym wydajniej bez tworzenia kwerendy LINQ, który wiąże obciążenie tworzenia kolekcji listy jako źródła danych. Przydatność podejście LINQ zwiększa się wraz ze wzrostem bardziej skomplikowane zapytanie, lub do wykonywania kwerend wiele do jednego źródła danych.  
  
 Zapytanie uwidacznia do oddzielnych metodach uzyskać długość pliku. Dzieje się tak, aby korzystać z możliwości wyjątek, który zostanie wygenerowany, jeśli plik został usunięty w innym wątku po <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Mimo że <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości o długości najbardziej aktualne przy pierwszym uzyskaniu dostępu do właściwości. Ustawiając tę operację w bloku try-catch poza zapytania, kod następuje reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne. Ogólnie rzecz biorąc szczególną uwagę należy podczas korzystania wyjątki, aby się upewnić, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
