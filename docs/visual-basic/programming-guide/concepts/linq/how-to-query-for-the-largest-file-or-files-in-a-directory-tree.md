---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 723a42e79f1def171a08b28986049ffa04945fc4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266992"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Jak: Zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)
W tym przykładzie przedstawiono pięć zapytań związanych z rozmiarem pliku w bajtach:  
  
- Jak pobrać rozmiar w bajtach największego pliku.  
  
- Jak pobrać rozmiar w bajtach najmniejszego pliku.  
  
- Jak pobrać <xref:System.IO.FileInfo> obiekt największy lub najmniejszy plik z jednego lub więcej folderów w określonym folderze głównym.  
  
- Jak pobrać sekwencję, taką jak 10 największych plików.  
  
- Jak zamówić pliki do grup na podstawie ich rozmiaru pliku w bajtach, ignorując pliki, które są mniejsze niż określony rozmiar.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak kwerendy i grupy plików, w zależności od ich rozmiaru pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby oprzeć <xref:System.IO.FileInfo> kwerendę na innej właściwości obiektu.  
  
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
  
 Aby zwrócić jeden <xref:System.IO.FileInfo> lub więcej kompletnych obiektów, kwerenda musi najpierw zbadać każdy z nich w źródle danych, a następnie posortować je według wartości ich Length właściwości. Następnie może zwrócić pojedynczy lub sekwencji o największych długościach. Służy <xref:System.Linq.Enumerable.First%2A> do zwracania pierwszego elementu na liście. Służy <xref:System.Linq.Enumerable.Take%2A> do zwracania pierwszej n liczby elementów. Określ malejącą kolejność sortowania, aby umieścić najmniejsze elementy na początku listy.  
  
 Kwerenda wywołuje oddzielną metodę, aby uzyskać rozmiar pliku w bajtach w celu wykorzystania możliwego wyjątku, który zostanie podniesiony <xref:System.IO.FileInfo> w przypadku, gdy `GetFiles`plik został usunięty w innym wątku w okresie czasu, ponieważ obiekt został utworzony w wywołaniu do . Nawet za <xref:System.IO.FileInfo> pośrednictwem obiektu został już utworzony, <xref:System.IO.FileInfo> wyjątek może wystąpić, ponieważ obiekt spróbuje odświeżyć jego <xref:System.IO.FileInfo.Length%2A> właściwość przy użyciu najbardziej bieżącego rozmiaru w bajtach przy pierwszym dostępie do właściwości. Umieszczając tę operację w bloku try-catch poza kwerendą, stosujemy regułę unikania operacji w kwerendach, które mogą powodować skutki uboczne. Ogólnie rzecz biorąc należy zwrócić szczególną uwagę podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compile-the-code"></a>Skompiluj kod  
Utwórz projekt aplikacji konsoli języka `Imports` Visual Basic z instrukcją dla obszaru nazw System.Linq.
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
