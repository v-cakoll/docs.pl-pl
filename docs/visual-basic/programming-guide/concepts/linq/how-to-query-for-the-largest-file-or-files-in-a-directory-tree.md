---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: fd1ec163685af539e644d9fb4a0845fdcb3e1b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)
Ten przykład przedstawia pięć zapytań dotyczących rozmiaru pliku w bajtach:  
  
-   Jak pobrać rozmiar w bajtach największy plik.  
  
-   Jak pobrać rozmiar w bajtach najmniejszy plik.  
  
-   Jak pobrać <xref:System.IO.FileInfo> największego lub najmniejszy plik obiektu z jednego lub więcej folderów w folderze określonym katalogu głównym.  
  
-   Jak pobrać sekwencji, takie jak 10 plików największy.  
  
-   Jak kolejności plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, które mają mniej niż określony rozmiar zostaną zignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby utworzyć zapytanie na niektóre inne właściwości <xref:System.IO.FileInfo> obiektu.  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Aby powrócić na zakończenie jednego lub więcej <xref:System.IO.FileInfo> obiekty zapytania najpierw musi sprawdzić każdą z nich w danych źródła i sortować je przez wartość właściwości ich długość. Następnie może zwrócić pojedynczego co najmniej sekwencji o największej długości. Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszy element na liście. Użyj <xref:System.Linq.Enumerable.Take%2A> do zwrócenia pierwsze n liczby elementów. Określ malejącej kolejności sortowania umieścić najmniejszą elementów na początku listy.  
  
 Zapytanie uwidacznia do oddzielnych metodach uzyskać rozmiar pliku w bajtach, aby można było korzystać z możliwości wyjątek, który zostanie wygenerowany, w przypadku, gdy plik został usunięty przez inny wątek w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Nawet za pomocą <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najnowszych rozmiar w bajtach przy pierwszym uzyskaniu dostępu do właściwości. Ustawiając tę operację w bloku try-catch poza zapytanie, firma Microsoft wykonaj reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne. Ogólnie rzecz biorąc szczególną uwagę należy podczas używania wyjątków, upewnij się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
