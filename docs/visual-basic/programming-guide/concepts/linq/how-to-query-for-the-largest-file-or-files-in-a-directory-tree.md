---
title: 'Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 7ba330b18020b7c3b823b70d0541cdda199aa898
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820728"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="3ed68-102">Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed68-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="3ed68-103">Ten przykład przedstawia pięć zapytań dotyczących rozmiar pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="3ed68-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="3ed68-104">Jak pobrać rozmiar w bajtach największy plik.</span><span class="sxs-lookup"><span data-stu-id="3ed68-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="3ed68-105">Jak pobrać rozmiar w bajtach najmniejszy plik.</span><span class="sxs-lookup"><span data-stu-id="3ed68-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="3ed68-106">Jak pobrać <xref:System.IO.FileInfo> pliku największą lub najmniejszą z jednego lub więcej folderów w folderze głównym określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ed68-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="3ed68-107">Jak pobrać sekwencji, np. 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="3ed68-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="3ed68-108">Jak kolejność plików do grup, w oparciu o ich rozmiar pliku w bajtach, pliki, których wartość jest mniejsza niż określony rozmiar zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="3ed68-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed68-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ed68-109">Example</span></span>  
 <span data-ttu-id="3ed68-110">Poniższy przykład zawiera pięć oddzielne zapytania, które pokazują, jak wykonać zapytanie i grupy plików, w zależności od ich rozmiar pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3ed68-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="3ed68-111">Można łatwo modyfikować te przykłady, aby utworzyć kwerendy na kilka innych właściwości <xref:System.IO.FileInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ed68-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="3ed68-112">Aby powrócić, wykonaj co najmniej jeden <xref:System.IO.FileInfo> obiektów, najpierw kwerendy należy zbadać każdej z nich dane źródła, a następnie posortuj je według wartości ich właściwości Length.</span><span class="sxs-lookup"><span data-stu-id="3ed68-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="3ed68-113">Następnie może zwrócić pojedynczego co najmniej sekwencji największy długości.</span><span class="sxs-lookup"><span data-stu-id="3ed68-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="3ed68-114">Użyj <xref:System.Linq.Enumerable.First%2A> aby powrócić do pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="3ed68-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="3ed68-115">Użyj <xref:System.Linq.Enumerable.Take%2A> zwracać n pierwszą liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="3ed68-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="3ed68-116">Określ malejącej kolejności sortowania umieścić najmniejszy elementów na początku listy.</span><span class="sxs-lookup"><span data-stu-id="3ed68-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="3ed68-117">Wywołuje zapytanie do oddzielnych metodach, aby uzyskać rozmiar pliku w bajtach w celu korzystania z możliwości wyjątek, który zostanie wygenerowany, w przypadku, w którym plik został usunięty w innym wątku w okresie od <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="3ed68-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="3ed68-118">Nawet za pośrednictwem <xref:System.IO.FileInfo> obiekt został już utworzony, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej bieżący rozmiar w bajtach po raz pierwszy uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ed68-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="3ed68-119">Przez umieszczenie tej operacji w bloku try / catch, poza zapytania, postępujemy zgodnie z reguły unikania operacji w zapytaniach, które mogą spowodować, że efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="3ed68-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="3ed68-120">Ogólnie rzecz biorąc doskonałe należy uważać podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="3ed68-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ed68-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3ed68-121">Compiling the Code</span></span>  
 <span data-ttu-id="3ed68-122">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="3ed68-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed68-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ed68-123">See also</span></span>

- [<span data-ttu-id="3ed68-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed68-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="3ed68-125">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed68-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
