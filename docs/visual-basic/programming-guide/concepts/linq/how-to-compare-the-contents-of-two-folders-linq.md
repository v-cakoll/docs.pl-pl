---
title: 'Instrukcje: Porównywanie zawartości dwóch folderów (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
ms.openlocfilehash: 668f72e2a891a9332093b97ebc927c156ad2087c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820298"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="7977a-102">Instrukcje: Porównywanie zawartości dwóch folderów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7977a-102">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="7977a-103">W tym przykładzie przedstawiono trzy sposoby, aby porównać dwa listach plików:</span><span class="sxs-lookup"><span data-stu-id="7977a-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
-   <span data-ttu-id="7977a-104">Przy użyciu zapytań dotyczących wartość logiczna określająca, czy plik dwóch list są identyczne.</span><span class="sxs-lookup"><span data-stu-id="7977a-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
-   <span data-ttu-id="7977a-105">Przy użyciu zapytań dotyczących wspólną do pobierania plików, które znajdują się w obu folderów.</span><span class="sxs-lookup"><span data-stu-id="7977a-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
-   <span data-ttu-id="7977a-106">Przy użyciu zapytań dotyczących różnicy do pobierania plików, które znajdują się w jednym folderze, ale nie drugiej.</span><span class="sxs-lookup"><span data-stu-id="7977a-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7977a-107">Techniki przedstawione w tym miejscu mogą być dostosowane do porównania sekwencje obiekty dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="7977a-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="7977a-108">`FileComparer` Klasy wyświetlane w tym miejscu przedstawiono sposób użycia klasy niestandardowej funkcji porównującej, wraz z standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="7977a-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="7977a-109">Klasa nie jest przeznaczona do użytku w rzeczywistych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="7977a-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="7977a-110">Po prostu używa nazwy i długość w bajtach każdego pliku w celu określenia, czy zawartość każdego folderu są identyczne.</span><span class="sxs-lookup"><span data-stu-id="7977a-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="7977a-111">W rzeczywistym scenariuszu należy modyfikować tego modułu porównującego do bardziej rygorystyczne sprawdzanie równości.</span><span class="sxs-lookup"><span data-stu-id="7977a-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7977a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7977a-112">Example</span></span>  
  
```vb  
Module CompareDirs  
    Public Sub Main()  
  
        ' Create two identical or different temporary folders   
        ' on a local drive and add files to them.  
        ' Then set these file paths accordingly.  
        Dim pathA As String = "C:\TestDir"  
        Dim pathB As String = "C:\TestDir2"  
  
        ' Take a snapshot of the file system.   
        Dim dir1 As New System.IO.DirectoryInfo(pathA)  
        Dim dir2 As New System.IO.DirectoryInfo(pathB)  
  
        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the FileCompare object we'll use in each query  
        Dim myFileCompare As New FileCompare  
  
        ' This query determines whether the two folders contain  
        ' identical file lists, based on the custom file comparer  
        ' that is defined in the FileCompare class.  
        ' The query executes immediately because it returns a bool.  
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)  
        If areIdentical = True Then  
            Console.WriteLine("The two folders are the same.")  
        Else  
            Console.WriteLine("The two folders are not the same.")  
        End If  
  
        ' Find common files in both folders. It produces a sequence and doesn't execute  
        ' until the foreach statement.  
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)  
  
        If queryCommonFiles.Count() > 0 Then  
  
            Console.WriteLine("The following files are in both folders:")  
            For Each fi As System.IO.FileInfo In queryCommonFiles  
                Console.WriteLine(fi.FullName)  
            Next  
        Else  
            Console.WriteLine("There are no common files in the two folders.")  
        End If  
  
        ' Find the set difference between the two folders.  
        ' For this example we only check one way.  
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)  
        Console.WriteLine("The following files are in dirA but not dirB:")  
        For Each fi As System.IO.FileInfo In queryDirAOnly  
            Console.WriteLine(fi.FullName)  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This implementation defines a very simple comparison  
    ' between two FileInfo objects. It only compares the name  
    ' of the files being compared and their length in bytes.  
    Public Class FileCompare  
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)  
  
        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _  
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals  
  
            If (x.Name = y.Name) And (x.Length = y.Length) Then  
                Return True  
            Else  
                Return False  
            End If  
        End Function  
  
        ' Return a hash that reflects the comparison criteria. According to the   
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must  
        ' also be equal. Because equality as defined here is a simple value equality, not  
        ' reference identity, it is possible that two or more objects will produce the same  
        ' hash code.  
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _  
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode  
            Dim s As String = fi.Name & fi.Length  
            Return s.GetHashCode()  
        End Function  
    End Class  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7977a-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7977a-113">Compiling the Code</span></span>  
 <span data-ttu-id="7977a-114">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji dla przestrzeni nazw System.Linq.</span><span class="sxs-lookup"><span data-stu-id="7977a-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7977a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7977a-115">See also</span></span>

- [<span data-ttu-id="7977a-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7977a-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="7977a-117">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7977a-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
