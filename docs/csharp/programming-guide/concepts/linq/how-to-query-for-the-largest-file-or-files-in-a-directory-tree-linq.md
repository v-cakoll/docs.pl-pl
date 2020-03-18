---
title: Jak wysyłać zapytania o największy plik lub pliki w drzewie katalogów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: ed7d610bd292be4062db89f3c94af280e851141f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168768"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Jak wysyłać zapytania o największy plik lub pliki w drzewie katalogów (LINQ) (C#)
W tym przykładzie przedstawiono pięć kwerend związanych z rozmiarem pliku w bajtach:  
  
- Jak pobrać rozmiar w bajtach największego pliku.  
  
- Jak pobrać rozmiar w bajtach najmniejszego pliku.  
  
- Jak pobrać <xref:System.IO.FileInfo> obiekt największy lub najmniejszy plik z jednego lub więcej folderów w określonym folderze głównym.  
  
- Jak pobrać sekwencję, taką jak 10 największych plików.  
  
- Jak uporządkować pliki w grupy na podstawie ich rozmiaru pliku w bajtach, ignorując pliki, które są mniejsze niż określony rozmiar.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielnych kwerend, które pokazują, jak kwerendy i grupowania plików, w zależności od ich rozmiaru pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby oprzeć <xref:System.IO.FileInfo> kwerendę na innej właściwości obiektu.  
  
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
  
 Aby zwrócić jeden <xref:System.IO.FileInfo> lub więcej kompletnych obiektów, kwerenda najpierw należy zbadać każdy z nich w źródle danych, a następnie posortować je według wartości ich Length właściwości. Następnie może zwrócić pojedynczy lub sekwencji z największych długości. Służy <xref:System.Linq.Enumerable.First%2A> do zwracania pierwszego elementu na liście. Służy <xref:System.Linq.Enumerable.Take%2A> do zwracania pierwszej n liczby elementów. Określ malejącą kolejność sortowania, aby umieścić najmniejsze elementy na początku listy.  
  
 Kwerenda wywołuje do oddzielnej metody, aby uzyskać rozmiar pliku w bajtach w celu użycia możliwego wyjątku, który zostanie podniesiony w przypadku, gdy plik został usunięty na inny wątek w okresie czasu, ponieważ <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Nawet za <xref:System.IO.FileInfo> pośrednictwem obiektu został już utworzony, <xref:System.IO.FileInfo> wyjątek może wystąpić, <xref:System.IO.FileInfo.Length%2A> ponieważ obiekt będzie próbował odświeżyć jego właściwości przy użyciu najbardziej bieżącego rozmiaru w bajtach przy pierwszym dostępie do właściwości. Umieszczając tę operację w bloku try-catch poza kwerendą, możemy przestrzegać reguły unikania operacji w kwerendach, które mogą powodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas używania wyjątków, aby upewnić się, że aplikacja nie pozostaje w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.

## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
