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
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="9ee76-102">Jak wysyłać zapytania o największy plik lub pliki w drzewie katalogów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9ee76-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="9ee76-103">W tym przykładzie przedstawiono pięć kwerend związanych z rozmiarem pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="9ee76-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="9ee76-104">Jak pobrać rozmiar w bajtach największego pliku.</span><span class="sxs-lookup"><span data-stu-id="9ee76-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="9ee76-105">Jak pobrać rozmiar w bajtach najmniejszego pliku.</span><span class="sxs-lookup"><span data-stu-id="9ee76-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="9ee76-106">Jak pobrać <xref:System.IO.FileInfo> obiekt największy lub najmniejszy plik z jednego lub więcej folderów w określonym folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="9ee76-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="9ee76-107">Jak pobrać sekwencję, taką jak 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="9ee76-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="9ee76-108">Jak uporządkować pliki w grupy na podstawie ich rozmiaru pliku w bajtach, ignorując pliki, które są mniejsze niż określony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="9ee76-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ee76-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ee76-109">Example</span></span>  
 <span data-ttu-id="9ee76-110">Poniższy przykład zawiera pięć oddzielnych kwerend, które pokazują, jak kwerendy i grupowania plików, w zależności od ich rozmiaru pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9ee76-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="9ee76-111">Można łatwo zmodyfikować te przykłady, aby oprzeć <xref:System.IO.FileInfo> kwerendę na innej właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ee76-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="9ee76-112">Aby zwrócić jeden <xref:System.IO.FileInfo> lub więcej kompletnych obiektów, kwerenda najpierw należy zbadać każdy z nich w źródle danych, a następnie posortować je według wartości ich Length właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ee76-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="9ee76-113">Następnie może zwrócić pojedynczy lub sekwencji z największych długości.</span><span class="sxs-lookup"><span data-stu-id="9ee76-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="9ee76-114">Służy <xref:System.Linq.Enumerable.First%2A> do zwracania pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="9ee76-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="9ee76-115">Służy <xref:System.Linq.Enumerable.Take%2A> do zwracania pierwszej n liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="9ee76-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="9ee76-116">Określ malejącą kolejność sortowania, aby umieścić najmniejsze elementy na początku listy.</span><span class="sxs-lookup"><span data-stu-id="9ee76-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="9ee76-117">Kwerenda wywołuje do oddzielnej metody, aby uzyskać rozmiar pliku w bajtach w celu użycia możliwego wyjątku, który zostanie podniesiony w przypadku, gdy plik został usunięty na inny wątek w okresie czasu, ponieważ <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="9ee76-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="9ee76-118">Nawet za <xref:System.IO.FileInfo> pośrednictwem obiektu został już utworzony, <xref:System.IO.FileInfo> wyjątek może wystąpić, <xref:System.IO.FileInfo.Length%2A> ponieważ obiekt będzie próbował odświeżyć jego właściwości przy użyciu najbardziej bieżącego rozmiaru w bajtach przy pierwszym dostępie do właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ee76-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="9ee76-119">Umieszczając tę operację w bloku try-catch poza kwerendą, możemy przestrzegać reguły unikania operacji w kwerendach, które mogą powodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="9ee76-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="9ee76-120">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas używania wyjątków, aby upewnić się, że aplikacja nie pozostaje w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="9ee76-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ee76-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9ee76-121">Compiling the Code</span></span>  
<span data-ttu-id="9ee76-122">Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9ee76-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ee76-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ee76-123">See also</span></span>

- [<span data-ttu-id="9ee76-124">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="9ee76-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="9ee76-125">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="9ee76-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
