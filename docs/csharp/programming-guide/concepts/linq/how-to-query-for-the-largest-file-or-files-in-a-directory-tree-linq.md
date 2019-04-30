---
title: 'Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 20453c754c792d4f5c59fde481e1fec56dcd0e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702285"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)
Ten przykład przedstawia pięć zapytań dotyczących rozmiar pliku w bajtach:  
  
- Jak pobrać rozmiar w bajtach największy plik.  
  
- Jak pobrać rozmiar w bajtach najmniejszy plik.  
  
- Jak pobrać <xref:System.IO.FileInfo> pliku największą lub najmniejszą z jednego lub więcej folderów w folderze głównym określonego obiektu.  
  
- Jak pobrać sekwencji, np. 10 największych plików.  
  
- Jak kolejność plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, których wartość jest mniejsza niż określony rozmiar zostaną zignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach. Można łatwo modyfikować te przykłady, aby utworzyć kwerendy na kilka innych właściwości <xref:System.IO.FileInfo> obiektu.  
  
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
  
 Aby powrócić, wykonaj co najmniej jeden <xref:System.IO.FileInfo> obiektów, najpierw kwerendy należy zbadać każdej z nich dane źródła, a następnie posortuj je według wartości ich właściwości Length. Następnie może zwrócić pojedynczego co najmniej sekwencji największy długości. Użyj <xref:System.Linq.Enumerable.First%2A> aby powrócić do pierwszego elementu na liście. Użyj <xref:System.Linq.Enumerable.Take%2A> zwracać n pierwszą liczbę elementów. Określ malejącej kolejności sortowania umieścić najmniejszy elementów na początku listy.  
  
 Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Nawet za pośrednictwem <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej bieżący rozmiar w bajtach po raz pierwszy uzyskano dostęp do właściwości. Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, postępujemy zgodnie z reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne. Ogólnie rzecz biorąc doskonałe należy uważać podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [LINQ i katalogi plików (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
