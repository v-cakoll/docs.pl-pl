---
title: 'Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 7ba330b18020b7c3b823b70d0541cdda199aa898
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820728"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)
Ten przykład przedstawia pięć zapytań dotyczących rozmiar pliku w bajtach:  
  
-   Jak pobrać rozmiar w bajtach największy plik.  
  
-   Jak pobrać rozmiar w bajtach najmniejszy plik.  
  
-   Jak pobrać <xref:System.IO.FileInfo> pliku największą lub najmniejszą z jednego lub więcej folderów w folderze głównym określonego obiektu.  
  
-   Jak pobrać sekwencji, np. 10 największych plików.  
  
-   Jak kolejność plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, których wartość jest mniejsza niż określony rozmiar zostaną zignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach. Można łatwo modyfikować te przykłady, aby utworzyć kwerendy na kilka innych właściwości <xref:System.IO.FileInfo> obiektu.  
  
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
  
 Aby powrócić, wykonaj co najmniej jeden <xref:System.IO.FileInfo> obiektów, najpierw kwerendy należy zbadać każdej z nich dane źródła, a następnie posortuj je według wartości ich właściwości Length. Następnie może zwrócić pojedynczego co najmniej sekwencji największy długości. Użyj <xref:System.Linq.Enumerable.First%2A> aby powrócić do pierwszego elementu na liście. Użyj <xref:System.Linq.Enumerable.Take%2A> zwracać n pierwszą liczbę elementów. Określ malejącej kolejności sortowania umieścić najmniejszy elementów na początku listy.  
  
 Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Nawet za pośrednictwem <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej bieżący rozmiar w bajtach po raz pierwszy uzyskano dostęp do właściwości. Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, postępujemy zgodnie z reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne. Ogólnie rzecz biorąc doskonałe należy uważać podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
