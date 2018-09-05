---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: cbdf02b8c3035b8db58238113debb273c6c9dc35
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506111"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="e9c06-102">Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e9c06-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="e9c06-103">Ten przykład przedstawia pięć zapytań dotyczących rozmiar pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="e9c06-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="e9c06-104">Jak pobrać rozmiar w bajtach największy plik.</span><span class="sxs-lookup"><span data-stu-id="e9c06-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="e9c06-105">Jak pobrać rozmiar w bajtach najmniejszy plik.</span><span class="sxs-lookup"><span data-stu-id="e9c06-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="e9c06-106">Jak pobrać <xref:System.IO.FileInfo> pliku największą lub najmniejszą z jednego lub więcej folderów w folderze głównym określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9c06-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="e9c06-107">Jak pobrać sekwencji, np. 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="e9c06-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="e9c06-108">Jak kolejność plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, których wartość jest mniejsza niż określony rozmiar zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="e9c06-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c06-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9c06-109">Example</span></span>  
 <span data-ttu-id="e9c06-110">Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e9c06-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="e9c06-111">Można łatwo modyfikować te przykłady, aby utworzyć kwerendy na kilka innych właściwości <xref:System.IO.FileInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9c06-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="e9c06-112">Aby powrócić, wykonaj co najmniej jeden <xref:System.IO.FileInfo> obiektów, najpierw kwerendy należy zbadać każdej z nich dane źródła, a następnie posortuj je według wartości ich właściwości Length.</span><span class="sxs-lookup"><span data-stu-id="e9c06-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="e9c06-113">Następnie może zwrócić pojedynczego co najmniej sekwencji największy długości.</span><span class="sxs-lookup"><span data-stu-id="e9c06-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="e9c06-114">Użyj <xref:System.Linq.Enumerable.First%2A> aby powrócić do pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="e9c06-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="e9c06-115">Użyj <xref:System.Linq.Enumerable.Take%2A> zwracać n pierwszą liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="e9c06-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="e9c06-116">Określ malejącej kolejności sortowania umieścić najmniejszy elementów na początku listy.</span><span class="sxs-lookup"><span data-stu-id="e9c06-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="e9c06-117">Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="e9c06-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="e9c06-118">Nawet za pośrednictwem <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej bieżący rozmiar w bajtach po raz pierwszy uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9c06-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="e9c06-119">Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, postępujemy zgodnie z reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="e9c06-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="e9c06-120">Ogólnie rzecz biorąc doskonałe należy uważać podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="e9c06-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e9c06-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e9c06-121">Compiling the Code</span></span>  
 <span data-ttu-id="e9c06-122">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="e9c06-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c06-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9c06-123">See Also</span></span>

- [<span data-ttu-id="e9c06-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e9c06-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="e9c06-125">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="e9c06-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
