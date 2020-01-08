---
title: Jak wykonać zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344817"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Jak wykonać zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)
Ten przykład pokazuje, jak pobrać łączną liczbę bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.  
  
## <a name="example"></a>Przykład  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> dodaje wartości wszystkich elementów wybranych w klauzuli `select`. Możesz łatwo zmodyfikować to zapytanie, aby pobrać największy lub najmniejszy plik w określonym drzewie katalogów, wywołując metodę <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Jeśli musisz tylko policzyć liczbę bajtów w określonym drzewie katalogów, możesz to zrobić bardziej wydajnie bez tworzenia zapytania LINQ, które wiąże się z obciążeniem tworzenia kolekcji list jako źródła danych. Użyteczność podejścia LINQ zwiększa się, gdy zapytanie jest bardziej złożone, lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.  
  
 Zapytanie wywołuje oddzielną metodę w celu uzyskania długości pliku. Wykonuje to w celu użycia możliwego wyjątku, który zostanie wywołany, jeśli plik został usunięty z innego wątku po utworzeniu obiektu <xref:System.IO.FileInfo> w wywołaniu `GetFiles`. Mimo że obiekt <xref:System.IO.FileInfo> został już utworzony, może wystąpić wyjątek, ponieważ obiekt <xref:System.IO.FileInfo> spróbuje odświeżyć jego właściwość <xref:System.IO.FileInfo.Length%2A> z największą aktualną długością podczas pierwszego dostępu do właściwości. Przez umieszczenie tej operacji w bloku try-catch poza zapytania, kod jest zgodny z regułą unikania operacji w zapytaniach, które mogą spowodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
