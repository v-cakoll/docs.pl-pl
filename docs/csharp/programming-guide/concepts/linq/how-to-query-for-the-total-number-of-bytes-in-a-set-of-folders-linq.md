---
title: 'Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 7a11e30a41ce171d516d3ea00a0e8664efe33520
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185931"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="5a5b7-102">Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5a5b7-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="5a5b7-103">Ten przykład przedstawia sposób pobierania całkowita liczba bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5b7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a5b7-104">Example</span></span>  
 <span data-ttu-id="5a5b7-105"><xref:System.Linq.Enumerable.Sum%2A> Metoda dodaje wartość wszystkie aby elementy wybierane w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="5a5b7-106">Można łatwo modyfikować to zapytanie, aby pobrać plik największą lub najmniejszą w drzewie katalogu określonego przez wywołanie metody <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast metody <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="5a5b7-107">Jeśli masz tylko liczbę bajtów w drzewie określonego katalogu, możesz to zrobić w wydajniej bez tworzenia zapytania LINQ, którą jest naliczana kłopotów z tworzeniem kolekcji list jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="5a5b7-108">Użyteczność podejście LINQ zwiększa zapytanie staje się bardziej złożone, lub gdy w celu uruchomienia wielu zapytań tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="5a5b7-109">Wywołuje zapytanie do oddzielnych metodach uzyskać długość pliku.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="5a5b7-110">Dzieje się tak aby można było korzystać z możliwych wyjątek, który zostanie wygenerowany, jeśli plik został usunięty w innym wątku po <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="5a5b7-111">Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości o długości najbardziej aktualne po raz pierwszy uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="5a5b7-112">Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, kod poniżej reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="5a5b7-113">Ogólnie rzecz biorąc doskonałe należy uważać, gdy wykorzystasz wyjątki, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a5b7-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5a5b7-114">Compiling the Code</span></span>  
 <span data-ttu-id="5a5b7-115">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5b7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a5b7-116">See Also</span></span>

- [<span data-ttu-id="5a5b7-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="5a5b7-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="5a5b7-118">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="5a5b7-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
