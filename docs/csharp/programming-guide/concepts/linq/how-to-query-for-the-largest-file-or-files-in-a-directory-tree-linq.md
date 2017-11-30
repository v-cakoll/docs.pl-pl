---
title: "Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ab52cc46a7d735ebe60f1d3822d5ae39c2a1234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a>Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)
Ten przykład przedstawia pięć zapytań dotyczących rozmiaru pliku w bajtach:  
  
-   Jak pobrać rozmiar w bajtach największy plik.  
  
-   Jak pobrać rozmiar w bajtach najmniejszy plik.  
  
-   Jak pobrać <xref:System.IO.FileInfo> największego lub najmniejszy plik obiektu z jednego lub więcej folderów w folderze określonym katalogu głównym.  
  
-   Jak pobrać sekwencji, takie jak 10 plików największy.  
  
-   Jak kolejności plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, które mają mniej niż określony rozmiar zostaną zignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach. Można łatwo zmodyfikować te przykłady, aby utworzyć zapytanie na niektóre inne właściwości <xref:System.IO.FileInfo> obiektu.  
  
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
  
 Aby powrócić na zakończenie jednego lub więcej <xref:System.IO.FileInfo> obiekty zapytania najpierw musi sprawdzić każdą z nich w danych źródła i sortować je przez wartość właściwości ich długość. Następnie może zwrócić pojedynczego co najmniej sekwencji o największej długości. Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszy element na liście. Użyj <xref:System.Linq.Enumerable.Take%2A> do zwrócenia pierwsze n liczby elementów. Określ malejącej kolejności sortowania umieścić najmniejszą elementów na początku listy.  
  
 Zapytanie uwidacznia do oddzielnych metodach uzyskać rozmiar pliku w bajtach, aby można było korzystać z możliwości wyjątek, który zostanie wygenerowany, w przypadku, gdy plik został usunięty przez inny wątek w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Nawet za pomocą <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najnowszych rozmiar w bajtach przy pierwszym uzyskaniu dostępu do właściwości. Ustawiając tę operację w bloku try-catch poza zapytanie, firma Microsoft wykonaj reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne. Ogólnie rzecz biorąc szczególną uwagę należy podczas używania wyjątków, upewnij się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [LINQ i katalogi plików (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
