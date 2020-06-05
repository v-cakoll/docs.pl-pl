---
title: 'Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c6490c8863b5762b0b487c6f3f3b2809e16d6519
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397937"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="2ed40-102">Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ed40-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="2ed40-103">Ten przykład pokazuje, jak pobrać łączną liczbę bajtów używanych przez wszystkie pliki w określonym folderze i jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="2ed40-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ed40-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ed40-104">Example</span></span>  
 <span data-ttu-id="2ed40-105"><xref:System.Linq.Enumerable.Sum%2A>Metoda dodaje wartości wszystkich elementów wybranych w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2ed40-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="2ed40-106">Możesz łatwo zmodyfikować to zapytanie, aby pobrać największy lub najmniejszy plik w określonym drzewie katalogów, wywołując <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> metodę or zamiast <xref:System.Linq.Enumerable.Sum%2A> .</span><span class="sxs-lookup"><span data-stu-id="2ed40-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="2ed40-107">Jeśli musisz tylko policzyć liczbę bajtów w określonym drzewie katalogów, możesz to zrobić bardziej wydajnie bez tworzenia zapytania LINQ, które wiąże się z obciążeniem tworzenia kolekcji list jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2ed40-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="2ed40-108">Użyteczność podejścia LINQ zwiększa się, gdy zapytanie jest bardziej złożone, lub gdy trzeba uruchomić wiele zapytań względem tego samego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2ed40-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="2ed40-109">Zapytanie wywołuje oddzielną metodę w celu uzyskania długości pliku.</span><span class="sxs-lookup"><span data-stu-id="2ed40-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="2ed40-110">Wykonuje to w celu użycia możliwego wyjątku, który zostanie wywołany, jeśli plik został usunięty z innego wątku po <xref:System.IO.FileInfo> utworzeniu obiektu w wywołaniu `GetFiles` .</span><span class="sxs-lookup"><span data-stu-id="2ed40-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="2ed40-111">Mimo że <xref:System.IO.FileInfo> obiekt został już utworzony, wyjątek może wystąpić, ponieważ <xref:System.IO.FileInfo> obiekt podejmie próbę odświeżenia swojej <xref:System.IO.FileInfo.Length%2A> właściwości z największą bieżącą długością dostępną do właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ed40-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="2ed40-112">Przez umieszczenie tej operacji w bloku try-catch poza zapytania, kod jest zgodny z regułą unikania operacji w zapytaniach, które mogą spowodować skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="2ed40-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="2ed40-113">Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas korzystania z wyjątków, aby upewnić się, że aplikacja nie jest pozostawiona w nieznanym stanie.</span><span class="sxs-lookup"><span data-stu-id="2ed40-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="2ed40-114">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="2ed40-114">Compile the code</span></span>  
<span data-ttu-id="2ed40-115">Utwórz projekt aplikacji konsolowej Visual Basic przy użyciu `Imports` instrukcji dla przestrzeni nazw System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ed40-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ed40-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ed40-116">See also</span></span>

- [<span data-ttu-id="2ed40-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ed40-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="2ed40-118">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ed40-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
