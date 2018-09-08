---
title: 'Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 7a11e30a41ce171d516d3ea00a0e8664efe33520
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135188"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)
Ten przykład przedstawia sposób pobierania całkowita liczba bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.  
  
## <a name="example"></a>Przykład  
 <xref:System.Linq.Enumerable.Sum%2A> Metoda dodaje wartość wszystkie aby elementy wybierane w `select` klauzuli. Można łatwo modyfikować to zapytanie, aby pobrać plik największą lub najmniejszą w drzewie katalogu określonego przez wywołanie metody <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast metody <xref:System.Linq.Enumerable.Sum%2A>.  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
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
  
 Jeśli masz tylko liczbę bajtów w drzewie określonego katalogu, możesz to zrobić w wydajniej bez tworzenia zapytania LINQ, którą jest naliczana kłopotów z tworzeniem kolekcji list jako źródła danych. Użyteczność podejście LINQ zwiększa zapytanie staje się bardziej złożone, lub gdy w celu uruchomienia wielu zapytań tego samego źródła danych.  
  
 Wywołuje zapytanie do oddzielnych metodach uzyskać długość pliku. Dzieje się tak aby można było korzystać z możliwych wyjątek, który zostanie wygenerowany, jeśli plik został usunięty w innym wątku po <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`. Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości o długości najbardziej aktualne po raz pierwszy uzyskano dostęp do właściwości. Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, kod poniżej reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne. Ogólnie rzecz biorąc doskonałe należy uważać, gdy wykorzystasz wyjątki, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [LINQ i katalogi plików (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
