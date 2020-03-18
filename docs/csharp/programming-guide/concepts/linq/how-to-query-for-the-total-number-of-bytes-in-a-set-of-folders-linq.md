---
title: Jak wysyłać zapytania o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: c6bfe6bb6d76e7ce8ea8887eef85cd64f2a025df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344817"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Jak zbadać całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)
W tym przykładzie pokazano, jak pobrać całkowitą liczbę bajtów używanych przez wszystkie pliki w określonym folderze i wszystkie jego podfoldery.  
  
## <a name="example"></a>Przykład  
 Metoda <xref:System.Linq.Enumerable.Sum%2A> dodaje wartości wszystkich elementów wybranych `select` w klauzuli. Można łatwo zmodyfikować tę kwerendę, aby pobrać największy lub najmniejszy <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> plik w <xref:System.Linq.Enumerable.Sum%2A>określonym drzewie katalogów, wywołując lub metody zamiast .  
  
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
  
 Jeśli trzeba tylko policzyć liczbę bajtów w drzewie określonego katalogu, można to zrobić bardziej efektywnie bez tworzenia kwerendy LINQ, która ponosi obciążenie tworzenia kolekcji listy jako źródła danych. Przydatność podejścia LINQ zwiększa się, gdy kwerenda staje się bardziej złożona lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.  
  
 Kwerenda wywołuje do oddzielnej metody, aby uzyskać długość pliku. Czyni to w celu użycia możliwego wyjątku, który zostanie podniesiony, <xref:System.IO.FileInfo> jeśli plik został usunięty `GetFiles`w innym wątku po utworzeniu obiektu w wywołaniu . Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek może <xref:System.IO.FileInfo> wystąpić, ponieważ <xref:System.IO.FileInfo.Length%2A> obiekt będzie próbował odświeżyć jego właściwość z najbardziej bieżącą długość przy pierwszym dostępie do właściwości. Umieszczając tę operację w bloku try-catch poza kwerendą, kod jest zgodny z regułą unikania operacji w kwerendach, które mogą powodować skutki uboczne. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas używania wyjątków, aby upewnić się, że aplikacja nie pozostaje w nieznanym stanie.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
