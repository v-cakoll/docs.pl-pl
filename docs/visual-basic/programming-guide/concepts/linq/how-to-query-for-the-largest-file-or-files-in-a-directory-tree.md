---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: fd1ec163685af539e644d9fb4a0845fdcb3e1b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643416"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="47c16-102">Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c16-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="47c16-103">Ten przykład przedstawia pięć zapytań dotyczących rozmiaru pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="47c16-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="47c16-104">Jak pobrać rozmiar w bajtach największy plik.</span><span class="sxs-lookup"><span data-stu-id="47c16-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="47c16-105">Jak pobrać rozmiar w bajtach najmniejszy plik.</span><span class="sxs-lookup"><span data-stu-id="47c16-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="47c16-106">Jak pobrać <xref:System.IO.FileInfo> największego lub najmniejszy plik obiektu z jednego lub więcej folderów w folderze określonym katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="47c16-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="47c16-107">Jak pobrać sekwencji, takie jak 10 plików największy.</span><span class="sxs-lookup"><span data-stu-id="47c16-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="47c16-108">Jak kolejności plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, które mają mniej niż określony rozmiar zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="47c16-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c16-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="47c16-109">Example</span></span>  
 <span data-ttu-id="47c16-110">Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="47c16-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="47c16-111">Można łatwo zmodyfikować te przykłady, aby utworzyć zapytanie na niektóre inne właściwości <xref:System.IO.FileInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="47c16-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="47c16-112">Aby powrócić na zakończenie jednego lub więcej <xref:System.IO.FileInfo> obiekty zapytania najpierw musi sprawdzić każdą z nich w danych źródła i sortować je przez wartość właściwości ich długość.</span><span class="sxs-lookup"><span data-stu-id="47c16-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="47c16-113">Następnie może zwrócić pojedynczego co najmniej sekwencji o największej długości.</span><span class="sxs-lookup"><span data-stu-id="47c16-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="47c16-114">Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszy element na liście.</span><span class="sxs-lookup"><span data-stu-id="47c16-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="47c16-115">Użyj <xref:System.Linq.Enumerable.Take%2A> do zwrócenia pierwsze n liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="47c16-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="47c16-116">Określ malejącej kolejności sortowania umieścić najmniejszą elementów na początku listy.</span><span class="sxs-lookup"><span data-stu-id="47c16-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="47c16-117">Zapytanie uwidacznia do oddzielnych metodach uzyskać rozmiar pliku w bajtach, aby można było korzystać z możliwości wyjątek, który zostanie wygenerowany, w przypadku, gdy plik został usunięty przez inny wątek w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="47c16-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="47c16-118">Nawet za pomocą <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najnowszych rozmiar w bajtach przy pierwszym uzyskaniu dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="47c16-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="47c16-119">Ustawiając tę operację w bloku try-catch poza zapytanie, firma Microsoft wykonaj reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="47c16-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="47c16-120">Ogólnie rzecz biorąc szczególną uwagę należy podczas używania wyjątków, upewnij się, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="47c16-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47c16-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="47c16-121">Compiling the Code</span></span>  
 <span data-ttu-id="47c16-122">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="47c16-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c16-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47c16-123">See Also</span></span>  
 [<span data-ttu-id="47c16-124">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c16-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="47c16-125">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c16-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
