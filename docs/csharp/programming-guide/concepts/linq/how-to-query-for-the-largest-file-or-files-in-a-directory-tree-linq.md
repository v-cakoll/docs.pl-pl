---
title: Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: dee501dc8d0cabd718307b45c99ca049ae4250aa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344563"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="f66fb-102">Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f66fb-102">How to query for the largest file or files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="f66fb-103">Ten przykład pokazuje pięć zapytań związanych z rozmiarem pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="f66fb-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="f66fb-104">Jak pobrać rozmiar w bajtach największego pliku.</span><span class="sxs-lookup"><span data-stu-id="f66fb-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="f66fb-105">Jak pobrać rozmiar w bajtach najmniejszego pliku.</span><span class="sxs-lookup"><span data-stu-id="f66fb-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="f66fb-106">Jak pobrać obiekt <xref:System.IO.FileInfo> największy lub najmniejszy z jednego lub kilku folderów w określonym folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="f66fb-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="f66fb-107">Jak pobrać sekwencję, taką jak 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="f66fb-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="f66fb-108">Jak zamówić pliki w grupach na podstawie ich rozmiaru pliku w bajtach, ignorowanie plików mniejszych niż określony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="f66fb-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f66fb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f66fb-109">Example</span></span>  
 <span data-ttu-id="f66fb-110">Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak wykonywać zapytania i grupować pliki, w zależności od rozmiaru pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f66fb-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="f66fb-111">Można łatwo zmodyfikować te przykłady, aby oprzeć zapytania na innej właściwości obiektu <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="f66fb-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="f66fb-112">Aby zwrócić jeden lub więcej kompletnych obiektów <xref:System.IO.FileInfo>, zapytanie najpierw musi zbadać każdy z nich w źródle danych, a następnie posortować je według wartości właściwości length.</span><span class="sxs-lookup"><span data-stu-id="f66fb-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="f66fb-113">Następnie może zwrócić jedną lub sekwencję o największą długość.</span><span class="sxs-lookup"><span data-stu-id="f66fb-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="f66fb-114">Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="f66fb-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="f66fb-115">Użyj <xref:System.Linq.Enumerable.Take%2A>, aby zwrócić pierwsze n liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="f66fb-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="f66fb-116">Określ malejący porządek sortowania, aby umieścić najmniejsze elementy na początku listy.</span><span class="sxs-lookup"><span data-stu-id="f66fb-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="f66fb-117">Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="f66fb-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="f66fb-118">Mimo że obiekt <xref:System.IO.FileInfo> został już utworzony, może wystąpić wyjątek, ponieważ obiekt <xref:System.IO.FileInfo> spróbuje odświeżyć jego właściwość <xref:System.IO.FileInfo.Length%2A> przy użyciu najbardziej aktualnego rozmiaru w bajtach przy pierwszym dostępie do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f66fb-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="f66fb-119">Przez umieszczenie tej operacji w bloku try-catch poza zapytaniem przestrzegamy zasad unikania operacji w zapytaniach, które mogą spowodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="f66fb-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="f66fb-120">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas zużywania wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="f66fb-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f66fb-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f66fb-121">Compiling the Code</span></span>  
<span data-ttu-id="f66fb-122">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.</span><span class="sxs-lookup"><span data-stu-id="f66fb-122">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="f66fb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f66fb-123">See also</span></span>

- [<span data-ttu-id="f66fb-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="f66fb-124">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="f66fb-125">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="f66fb-125">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
