---
title: 'Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: 6a6babaf019cdac2298aee6eff55581bf35b2e47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="b329f-102">Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b329f-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="b329f-103">W tym przykładzie pokazano, jak pobrać całkowita liczba bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="b329f-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b329f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b329f-104">Example</span></span>  
 <span data-ttu-id="b329f-105"><xref:System.Linq.Enumerable.Sum%2A> Metoda dodaje wartości wszystkich elementów wybranych w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b329f-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="b329f-106">Można łatwo zmodyfikować tego zapytania w celu pobrania plików największych lub najmniejszą w drzewie katalogu określonego przez wywołanie metody <xref:System.Linq.Enumerable.Min%2A> lub <xref:System.Linq.Enumerable.Max%2A> zamiast metody <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="b329f-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="b329f-107">Jeśli masz tylko liczbę bajtów w drzewie określonego katalogu, można w tym wydajniej bez tworzenia kwerendy LINQ, który wiąże obciążenie tworzenia kolekcji listy jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b329f-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="b329f-108">Przydatność podejście LINQ zwiększa się wraz ze wzrostem bardziej skomplikowane zapytanie, lub do wykonywania kwerend wiele do jednego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b329f-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="b329f-109">Zapytanie uwidacznia do oddzielnych metodach uzyskać długość pliku.</span><span class="sxs-lookup"><span data-stu-id="b329f-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="b329f-110">Dzieje się tak, aby korzystać z możliwości wyjątek, który zostanie wygenerowany, jeśli plik został usunięty w innym wątku po <xref:System.IO.FileInfo> obiekt został utworzony w wywołaniu `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="b329f-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="b329f-111">Mimo że <xref:System.IO.FileInfo> obiekt już istnieje, może wystąpić wyjątek ponieważ <xref:System.IO.FileInfo> obiektu podejmie próbę odświeżenia jego <xref:System.IO.FileInfo.Length%2A> właściwości o długości najbardziej aktualne przy pierwszym uzyskaniu dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b329f-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="b329f-112">Ustawiając tę operację w bloku try-catch poza zapytania, kod następuje reguły unikania operacji w zapytaniach, które mogą powodować efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="b329f-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="b329f-113">Ogólnie rzecz biorąc szczególną uwagę należy podczas korzystania wyjątki, aby się upewnić, że aplikacja nie pozostanie w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="b329f-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b329f-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b329f-114">Compiling the Code</span></span>  
 <span data-ttu-id="b329f-115">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b329f-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b329f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b329f-116">See Also</span></span>  
 [<span data-ttu-id="b329f-117">LINQ do obiektów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b329f-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="b329f-118">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b329f-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
