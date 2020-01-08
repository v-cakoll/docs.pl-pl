---
title: Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: dee501dc8d0cabd718307b45c99ca049ae4250aa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344563"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)
Ten przykład pokazuje pięć zapytań związanych z rozmiarem pliku w bajtach:  
  
- Jak pobrać rozmiar w bajtach największego pliku.  
  
- Jak pobrać rozmiar w bajtach najmniejszego pliku.  
  
- Jak pobrać obiekt <xref:System.IO.FileInfo> największy lub najmniejszy z jednego lub kilku folderów w określonym folderze głównym.  
  
- Jak pobrać sekwencję, taką jak 10 największych plików.  
  
- Jak zamówić pliki w grupach na podstawie ich rozmiaru pliku w bajtach, ignorowanie plików mniejszych niż określony rozmiar.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak wykonywać zapytania i grupować pliki, w zależności od rozmiaru pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby oprzeć zapytania na innej właściwości obiektu <xref:System.IO.FileInfo>.  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
  
}  
```  
  
 Aby zwrócić jeden lub więcej kompletnych obiektów <xref:System.IO.FileInfo>, zapytanie najpierw musi zbadać każdy z nich w źródle danych, a następnie posortować je według wartości właściwości length. Następnie może zwrócić jedną lub sekwencję o największą długość. Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszego elementu na liście. Użyj <xref:System.Linq.Enumerable.Take%2A>, aby zwrócić pierwsze n liczbę elementów. Określ malejący porządek sortowania, aby umieścić najmniejsze elementy na początku listy.  
  
 Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Mimo że obiekt <xref:System.IO.FileInfo> został już utworzony, może wystąpić wyjątek, ponieważ obiekt <xref:System.IO.FileInfo> spróbuje odświeżyć jego właściwość <xref:System.IO.FileInfo.Length%2A> przy użyciu najbardziej aktualnego rozmiaru w bajtach przy pierwszym dostępie do tej właściwości. Przez umieszczenie tej operacji w bloku try-catch poza zapytaniem przestrzegamy zasad unikania operacji w zapytaniach, które mogą spowodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas zużywania wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.
 
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
