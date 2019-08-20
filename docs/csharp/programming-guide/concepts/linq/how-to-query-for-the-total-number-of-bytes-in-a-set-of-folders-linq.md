---
title: 'Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 2db979c10eae9ecc5d4e154ae58248ca95a7cdc3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592734"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="39de3-102">Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="39de3-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="39de3-103">Ten przykład pokazuje, jak pobrać łączną liczbę bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="39de3-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39de3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="39de3-104">Example</span></span>  
 <span data-ttu-id="39de3-105">Metoda dodaje wartości wszystkich elementów wybranych `select` w klauzuli. <xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="39de3-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="39de3-106">Możesz łatwo zmodyfikować to zapytanie, aby pobrać największy lub najmniejszy plik w określonym drzewie katalogów, wywołując <xref:System.Linq.Enumerable.Min%2A> metodę or <xref:System.Linq.Enumerable.Max%2A> zamiast <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="39de3-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="39de3-107">Jeśli musisz tylko policzyć liczbę bajtów w określonym drzewie katalogów, możesz to zrobić bardziej wydajnie bez tworzenia zapytania LINQ, które wiąże się z obciążeniem tworzenia kolekcji list jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="39de3-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="39de3-108">Użyteczność podejścia LINQ zwiększa się, gdy zapytanie jest bardziej złożone, lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="39de3-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="39de3-109">Zapytanie wywołuje oddzielną metodę w celu uzyskania długości pliku.</span><span class="sxs-lookup"><span data-stu-id="39de3-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="39de3-110">Wykonuje to w celu użycia możliwego wyjątku, który zostanie wywołany, jeśli plik został usunięty z innego wątku po <xref:System.IO.FileInfo> utworzeniu obiektu w `GetFiles`wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="39de3-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="39de3-111">Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek może wystąpić, <xref:System.IO.FileInfo> ponieważ obiekt podejmie próbę odświeżenia swojej <xref:System.IO.FileInfo.Length%2A> właściwości z największą bieżącą długością dostępną do właściwości.</span><span class="sxs-lookup"><span data-stu-id="39de3-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="39de3-112">Przez umieszczenie tej operacji w bloku try-catch poza zapytania, kod jest zgodny z regułą unikania operacji w zapytaniach, które mogą spowodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="39de3-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="39de3-113">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="39de3-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="39de3-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="39de3-114">Compiling the Code</span></span>  
<span data-ttu-id="39de3-115">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="39de3-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="39de3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39de3-116">See also</span></span>

- [<span data-ttu-id="39de3-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="39de3-117">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="39de3-118">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="39de3-118">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
