---
title: 'Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 107f3457fe7361fab16c2c8ce837c90484fc7633
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397950"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)
Ten przykład pokazuje pięć zapytań związanych z rozmiarem pliku w bajtach:  
  
- Jak pobrać rozmiar w bajtach największego pliku.  
  
- Jak pobrać rozmiar w bajtach najmniejszego pliku.  
  
- Jak pobrać <xref:System.IO.FileInfo> największy lub najmniejszy plik z co najmniej jednego folderu w określonym folderze głównym.  
  
- Jak pobrać sekwencję, taką jak 10 największych plików.  
  
- Jak zamówić pliki w grupach na podstawie ich rozmiaru pliku w bajtach, ignorowanie plików mniejszych niż określony rozmiar.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak wykonywać zapytania i grupować pliki, w zależności od rozmiaru pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby oprzeć zapytania na innej właściwości <xref:System.IO.FileInfo> obiektu.  
  
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
  
 Aby zwrócić jeden lub więcej kompletnych <xref:System.IO.FileInfo> obiektów, zapytanie najpierw musi zbadać każdy z nich w źródle danych, a następnie posortować je według wartości właściwości length. Następnie może zwrócić jedną lub sekwencję o największą długość. Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszego elementu na liście. Użyj, <xref:System.Linq.Enumerable.Take%2A> Aby zwrócić pierwsze n liczbę elementów. Określ malejący porządek sortowania, aby umieścić najmniejsze elementy na początku listy.  
  
 Zapytanie wywołuje oddzielną metodę w celu uzyskania rozmiaru pliku w bajtach, aby można było wykorzystać możliwy wyjątek, który zostanie wywołany w przypadku, gdy plik został usunięty z innego wątku w czasie, ponieważ <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles` . Nawet za pośrednictwem <xref:System.IO.FileInfo> obiektu został już utworzony, wyjątek może wystąpić, ponieważ <xref:System.IO.FileInfo> obiekt podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej aktualnego rozmiaru w bajtach przy pierwszym dostępie do tej właściwości. Przez umieszczenie tej operacji w bloku try-catch poza zapytaniem przestrzegamy zasad unikania operacji w zapytaniach, które mogą spowodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas zużywania wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compile-the-code"></a>Kompiluj kod  
Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu `Imports` instrukcji dla przestrzeni nazw System. LINQ.
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](linq-and-file-directories.md)
