---
title: 'Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ)'
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 723a42e79f1def171a08b28986049ffa04945fc4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266992"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="c58ef-102">Jak: Zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c58ef-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c58ef-103">W tym przykładzie przedstawiono pięć zapytań związanych z rozmiarem pliku w bajtach:</span><span class="sxs-lookup"><span data-stu-id="c58ef-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="c58ef-104">Jak pobrać rozmiar w bajtach największego pliku.</span><span class="sxs-lookup"><span data-stu-id="c58ef-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="c58ef-105">Jak pobrać rozmiar w bajtach najmniejszego pliku.</span><span class="sxs-lookup"><span data-stu-id="c58ef-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="c58ef-106">Jak pobrać <xref:System.IO.FileInfo> obiekt największy lub najmniejszy plik z jednego lub więcej folderów w określonym folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="c58ef-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="c58ef-107">Jak pobrać sekwencję, taką jak 10 największych plików.</span><span class="sxs-lookup"><span data-stu-id="c58ef-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="c58ef-108">Jak zamówić pliki do grup na podstawie ich rozmiaru pliku w bajtach, ignorując pliki, które są mniejsze niż określony rozmiar.</span><span class="sxs-lookup"><span data-stu-id="c58ef-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c58ef-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c58ef-109">Example</span></span>  
 <span data-ttu-id="c58ef-110">Poniższy przykład zawiera pięć oddzielnych zapytań, które pokazują, jak kwerendy i grupy plików, w zależności od ich rozmiaru pliku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="c58ef-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="c58ef-111">Można łatwo zmodyfikować te przykłady, aby oprzeć <xref:System.IO.FileInfo> kwerendę na innej właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="c58ef-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="c58ef-112">Aby zwrócić jeden <xref:System.IO.FileInfo> lub więcej kompletnych obiektów, kwerenda musi najpierw zbadać każdy z nich w źródle danych, a następnie posortować je według wartości ich Length właściwości.</span><span class="sxs-lookup"><span data-stu-id="c58ef-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="c58ef-113">Następnie może zwrócić pojedynczy lub sekwencji o największych długościach.</span><span class="sxs-lookup"><span data-stu-id="c58ef-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="c58ef-114">Służy <xref:System.Linq.Enumerable.First%2A> do zwracania pierwszego elementu na liście.</span><span class="sxs-lookup"><span data-stu-id="c58ef-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="c58ef-115">Służy <xref:System.Linq.Enumerable.Take%2A> do zwracania pierwszej n liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="c58ef-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="c58ef-116">Określ malejącą kolejność sortowania, aby umieścić najmniejsze elementy na początku listy.</span><span class="sxs-lookup"><span data-stu-id="c58ef-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="c58ef-117">Kwerenda wywołuje oddzielną metodę, aby uzyskać rozmiar pliku w bajtach w celu wykorzystania możliwego wyjątku, który zostanie podniesiony <xref:System.IO.FileInfo> w przypadku, gdy `GetFiles`plik został usunięty w innym wątku w okresie czasu, ponieważ obiekt został utworzony w wywołaniu do .</span><span class="sxs-lookup"><span data-stu-id="c58ef-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="c58ef-118">Nawet za <xref:System.IO.FileInfo> pośrednictwem obiektu został już utworzony, <xref:System.IO.FileInfo> wyjątek może wystąpić, ponieważ obiekt spróbuje odświeżyć jego <xref:System.IO.FileInfo.Length%2A> właściwość przy użyciu najbardziej bieżącego rozmiaru w bajtach przy pierwszym dostępie do właściwości.</span><span class="sxs-lookup"><span data-stu-id="c58ef-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="c58ef-119">Umieszczając tę operację w bloku try-catch poza kwerendą, stosujemy regułę unikania operacji w kwerendach, które mogą powodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="c58ef-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="c58ef-120">Ogólnie rzecz biorąc należy zwrócić szczególną uwagę podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="c58ef-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="c58ef-121">Skompiluj kod</span><span class="sxs-lookup"><span data-stu-id="c58ef-121">Compile the code</span></span>  
<span data-ttu-id="c58ef-122">Utwórz projekt aplikacji konsoli języka `Imports` Visual Basic z instrukcją dla obszaru nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="c58ef-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c58ef-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c58ef-123">See also</span></span>

- [<span data-ttu-id="c58ef-124">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c58ef-124">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="c58ef-125">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c58ef-125">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
