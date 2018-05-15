---
title: 'Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
ms.openlocfilehash: 19b542e22aa6e987a21095025a136d7602057b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="a3ffb-102">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3ffb-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="a3ffb-103">Ten przykład przedstawia sposób Scalanie zawartości dwóch plików, a następnie utworzyć zestaw nowych plików, które organizowania danych w nowy sposób.</span><span class="sxs-lookup"><span data-stu-id="a3ffb-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="a3ffb-104">Aby utworzyć pliki danych</span><span class="sxs-lookup"><span data-stu-id="a3ffb-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="a3ffb-105">Skopiuj te nazwy do pliku tekstowego o nazwie names1.txt i zapisz go w folderze projektu:</span><span class="sxs-lookup"><span data-stu-id="a3ffb-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2.  <span data-ttu-id="a3ffb-106">Skopiuj te nazwy do pliku tekstowego o nazwie names2.txt, a następnie zapisz go w folderze projektu: należy pamiętać, że oba pliki mają niektóre nazwy wspólnych.</span><span class="sxs-lookup"><span data-stu-id="a3ffb-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="a3ffb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3ffb-107">Example</span></span>  
  
```vb  
Class SplitWithGroups  
  
    Shared Sub Main()  
  
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Concatenate and remove duplicate names based on  
        Dim mergeQuery As IEnumerable(Of String) = fileA.Union(fileB)  
  
        ' Group the names by the first letter in the last name  
        Dim groupQuery = From name In mergeQuery   
                     Let n = name.Split(New Char() {","})   
                     Order By n(0)   
                     Group By groupKey = n(0)(0)   
                     Into groupName = Group  
  
        ' Create a new file for each group that was created  
        ' Note that nested foreach loops are required to access  
        ' individual items with each group.  
        For Each gGroup In groupQuery  
            Dim fileName As String = "..'..'..'testFile_" & gGroup.groupKey & ".txt"  
            Dim sw As New System.IO.StreamWriter(fileName)  
            Console.WriteLine(gGroup.groupKey)  
            For Each item In gGroup.groupName  
                Console.WriteLine("   " & item.name)  
                sw.WriteLine(item.name)  
            Next  
            sw.Close()  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Class  
' Console Output:  
' A  
'    Aw, Kam Foo  
' B  
'    Bankov, Peter  
'    Beebe, Ann  
' E  
'    El Yassir, Mehdi  
' G  
'    Garcia, Hugo  
'    Garcia, Debra  
'    Giakoumakis, Leo  
'    Gilchrist, Beth  
'    Guy, Wey Yuan  
' H  
'    Holm, Michael  
' L  
'    Liu, Jinghao  
' M  
'    McLin, Nkenge  
'    Myrcha, Jacek  
' N  
'    Noriega, Fabricio  
' P  
'    Potra, Cristina  
' T  
'    Toyoshima, Tim  
```  
  
 <span data-ttu-id="a3ffb-108">Program zapisuje oddzielny plik dla każdej grupy, w tym samym folderze co pliki danych.</span><span class="sxs-lookup"><span data-stu-id="a3ffb-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3ffb-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a3ffb-109">Compiling the Code</span></span>  
 <span data-ttu-id="a3ffb-110">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a3ffb-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ffb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3ffb-111">See Also</span></span>  
 [<span data-ttu-id="a3ffb-112">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3ffb-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="a3ffb-113">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3ffb-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
