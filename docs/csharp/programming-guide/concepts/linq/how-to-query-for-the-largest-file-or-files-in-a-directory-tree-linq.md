---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 004726c4df1af5a12a411d26c4dc36e1836597ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325360"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="b0f15-102">Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f15-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="b0f15-103">Ten przykład przedstawia pięć zapytań dotyczących rozmiaru pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="b0f15-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="b0f15-104">Jak pobrać rozmiar w bajtach największy plik.</span><span class="sxs-lookup"><span data-stu-id="b0f15-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="b0f15-105">Jak pobrać rozmiar w bajtach najmniejszy plik.</span><span class="sxs-lookup"><span data-stu-id="b0f15-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="b0f15-106">Jak pobrać <xref:System.IO.FileInfo> największego lub najmniejszy plik obiektu z jednego lub więcej folderów w folderze określonym katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="b0f15-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="b0f15-107">Jak pobrać sekwencji, takie jak 10 plików największy.</span><span class="sxs-lookup"><span data-stu-id="b0f15-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="b0f15-108">Jak kolejności plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, które mają mniej niż określony rozmiar zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="b0f15-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f15-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0f15-109">Example</span></span>  
 <span data-ttu-id="b0f15-110">Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b0f15-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="b0f15-111">Można łatwo zmodyfikować te przykłady, aby utworzyć zapytanie na niektóre inne właściwości <xref:System.IO.FileInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b0f15-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="b0f15-112">Aby powrócić na zakończenie jednego lub więcej <xref:System.IO.FileInfo> obiekty zapytania najpierw musi sprawdzić każdą z nich w danych źródła i sortować je przez wartość właściwości ich długość.</span><span class="sxs-lookup"><span data-stu-id="b0f15-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="b0f15-113">Następnie może zwrócić pojedynczego co najmniej sekwencji o największej długości.</span><span class="sxs-lookup"><span data-stu-id="b0f15-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="b0f15-114">Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszy element na liście.</span><span class="sxs-lookup"><span data-stu-id="b0f15-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="b0f15-115">Użyj <xref:System.Linq.Enumerable.Take%2A> do zwrócenia pierwsze n liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="b0f15-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="b0f15-116">Określ malejącej kolejności sortowania umieścić najmniejszą elementów na początku listy.</span><span class="sxs-lookup"><span data-stu-id="b0f15-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="b0f15-117">Zapytanie uwidacznia do oddzielnych metodach uzyskać rozmiar pliku w bajtach, aby można było korzystać z możliwości wyjątek, który zostanie wygenerowany, w przypadku, gdy plik został usunięty przez inny wątek w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="b0f15-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="b0f15-118">Nawet za pomocą <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najnowszych rozmiar w bajtach przy pierwszym uzyskaniu dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0f15-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="b0f15-119">Ustawiając tę operację w bloku try-catch poza zapytanie, firma Microsoft wykonaj reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="b0f15-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="b0f15-120">Ogólnie rzecz biorąc szczególną uwagę należy podczas używania wyjątków, upewnij się, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="b0f15-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0f15-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b0f15-121">Compiling the Code</span></span>  
 <span data-ttu-id="b0f15-122">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="b0f15-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f15-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0f15-123">See Also</span></span>  
 [<span data-ttu-id="b0f15-124">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f15-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="b0f15-125">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f15-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
