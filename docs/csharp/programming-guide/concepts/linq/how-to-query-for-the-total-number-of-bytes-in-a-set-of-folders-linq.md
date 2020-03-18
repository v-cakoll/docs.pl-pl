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
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="b4bf5-102">Jak zbadać całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b4bf5-102">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>
<span data-ttu-id="b4bf5-103">W tym przykładzie pokazano, jak pobrać całkowitą liczbę bajtów używanych przez wszystkie pliki w określonym folderze i wszystkie jego podfoldery.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4bf5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4bf5-104">Example</span></span>  
 <span data-ttu-id="b4bf5-105">Metoda <xref:System.Linq.Enumerable.Sum%2A> dodaje wartości wszystkich elementów wybranych `select` w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="b4bf5-106">Można łatwo zmodyfikować tę kwerendę, aby pobrać największy lub najmniejszy <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> plik w <xref:System.Linq.Enumerable.Sum%2A>określonym drzewie katalogów, wywołując lub metody zamiast .</span><span class="sxs-lookup"><span data-stu-id="b4bf5-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="b4bf5-107">Jeśli trzeba tylko policzyć liczbę bajtów w drzewie określonego katalogu, można to zrobić bardziej efektywnie bez tworzenia kwerendy LINQ, która ponosi obciążenie tworzenia kolekcji listy jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="b4bf5-108">Przydatność podejścia LINQ zwiększa się, gdy kwerenda staje się bardziej złożona lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="b4bf5-109">Kwerenda wywołuje do oddzielnej metody, aby uzyskać długość pliku.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="b4bf5-110">Czyni to w celu użycia możliwego wyjątku, który zostanie podniesiony, <xref:System.IO.FileInfo> jeśli plik został usunięty `GetFiles`w innym wątku po utworzeniu obiektu w wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="b4bf5-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="b4bf5-111">Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek może <xref:System.IO.FileInfo> wystąpić, ponieważ <xref:System.IO.FileInfo.Length%2A> obiekt będzie próbował odświeżyć jego właściwość z najbardziej bieżącą długość przy pierwszym dostępie do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="b4bf5-112">Umieszczając tę operację w bloku try-catch poza kwerendą, kod jest zgodny z regułą unikania operacji w kwerendach, które mogą powodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="b4bf5-113">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas używania wyjątków, aby upewnić się, że aplikacja nie pozostaje w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4bf5-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b4bf5-114">Compiling the Code</span></span>  
<span data-ttu-id="b4bf5-115">Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4bf5-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b4bf5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4bf5-116">See also</span></span>

- [<span data-ttu-id="b4bf5-117">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="b4bf5-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="b4bf5-118">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="b4bf5-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
