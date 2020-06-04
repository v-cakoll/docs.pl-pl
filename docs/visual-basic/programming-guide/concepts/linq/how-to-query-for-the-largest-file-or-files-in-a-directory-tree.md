---
title: 'Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 107f3457fe7361fab16c2c8ce837c90484fc7633
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397950"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="64011-102">Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64011-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="64011-103">Ten przykład pokazuje pięć zapytań związanych z rozmiarem pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="64011-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="64011-104">Jak pobrać rozmiar w bajtach największego pliku.</span><span class="sxs-lookup"><span data-stu-id="64011-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="64011-105">Jak pobrać rozmiar w bajtach najmniejszego pliku.</span><span class="sxs-lookup"><span data-stu-id="64011-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="64011-106">Jak pobrać <xref:System.IO.FileInfo> największy lub najmniejszy plik z co najmniej jednego folderu w określonym folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="64011-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="64011-107">Jak pobrać sekwencję, taką jak 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="64011-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="64011-108">Jak zamówić pliki w grupach na podstawie ich rozmiaru pliku w bajtach, ignorowanie plików mniejszych niż określony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="64011-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64011-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="64011-109">Example</span></span>  
 <span data-ttu-id="64011-110">Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak wykonywać zapytania i grupować pliki, w zależności od rozmiaru pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="64011-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="64011-111">Można łatwo zmodyfikować te przykłady, aby oprzeć zapytania na innej właściwości <xref:System.IO.FileInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="64011-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="64011-112">Aby zwrócić jeden lub więcej kompletnych <xref:System.IO.FileInfo> obiektów, zapytanie najpierw musi zbadać każdy z nich w źródle danych, a następnie posortować je według wartości właściwości length.</span><span class="sxs-lookup"><span data-stu-id="64011-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="64011-113">Następnie może zwrócić jedną lub sekwencję o największą długość.</span><span class="sxs-lookup"><span data-stu-id="64011-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="64011-114">Użyj <xref:System.Linq.Enumerable.First%2A> do zwrócenia pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="64011-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="64011-115">Użyj, <xref:System.Linq.Enumerable.Take%2A> Aby zwrócić pierwsze n liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="64011-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="64011-116">Określ malejący porządek sortowania, aby umieścić najmniejsze elementy na początku listy.</span><span class="sxs-lookup"><span data-stu-id="64011-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="64011-117">Zapytanie wywołuje oddzielną metodę w celu uzyskania rozmiaru pliku w bajtach, aby można było wykorzystać możliwy wyjątek, który zostanie wywołany w przypadku, gdy plik został usunięty z innego wątku w czasie, ponieważ <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles` .</span><span class="sxs-lookup"><span data-stu-id="64011-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="64011-118">Nawet za pośrednictwem <xref:System.IO.FileInfo> obiektu został już utworzony, wyjątek może wystąpić, ponieważ <xref:System.IO.FileInfo> obiekt podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości przy użyciu najbardziej aktualnego rozmiaru w bajtach przy pierwszym dostępie do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="64011-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="64011-119">Przez umieszczenie tej operacji w bloku try-catch poza zapytaniem przestrzegamy zasad unikania operacji w zapytaniach, które mogą spowodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="64011-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="64011-120">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas zużywania wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="64011-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="64011-121">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="64011-121">Compile the code</span></span>  
<span data-ttu-id="64011-122">Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu `Imports` instrukcji dla przestrzeni nazw System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="64011-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="64011-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64011-123">See also</span></span>

- [<span data-ttu-id="64011-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64011-124">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="64011-125">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64011-125">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
