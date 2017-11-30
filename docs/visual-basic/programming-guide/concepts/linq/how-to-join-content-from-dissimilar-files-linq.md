---
title: "Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7530857-c467-41ea-9730-84e6b1065a4d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 00a3e776afbed3fd87a1f91eb83ada5d505aadfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-join-content-from-dissimilar-files-linq-visual-basic"></a><span data-ttu-id="a5bb6-102">Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5bb6-102">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="a5bb6-103">W tym przykładzie pokazano, jak sprzęgać dane z dwóch plików rozdzielanych przecinkami, które mają wspólną wartość, które jest używane jako dopasowany klucz.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-103">This example shows how to join data from two comma-delimited files that share a common value that is used as a matching key.</span></span> <span data-ttu-id="a5bb6-104">Ta metoda może być przydatna, jeśli masz połączyć dane z dwóch arkuszy kalkulacyjnych lub z arkusza kalkulacyjnego i z pliku innego formatu, który ma do nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-104">This technique can be useful if you have to combine data from two spreadsheets, or from a spreadsheet and from a file that has another format, into a new file.</span></span> <span data-ttu-id="a5bb6-105">Można zmodyfikować przykładu do pracy z dowolnego rodzaju strukturalnych tekstu.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-105">You can modify the example to work with any kind of structured text.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="a5bb6-106">Aby utworzyć pliki danych</span><span class="sxs-lookup"><span data-stu-id="a5bb6-106">To create the data files</span></span>  
  
1.  <span data-ttu-id="a5bb6-107">Skopiuj następujące wiersze do pliku o nazwie scores.csv i zapisać go w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-107">Copy the following lines into a file that is named scores.csv and save it to your project folder.</span></span> <span data-ttu-id="a5bb6-108">Plik reprezentuje dane w arkuszu.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-108">The file represents spreadsheet data.</span></span> <span data-ttu-id="a5bb6-109">Kolumna 1 jest Identyfikatorem Studenta, a kolumny od 2 do 5 są wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-109">Column 1 is the student's ID, and columns 2 through 5 are test scores.</span></span>  
  
    ```  
    111, 97, 92, 81, 60  
    112, 75, 84, 91, 39  
    113, 88, 94, 65, 91  
    114, 97, 89, 85, 82  
    115, 35, 72, 91, 70  
    116, 99, 86, 90, 94  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    119, 68, 79, 88, 92  
    120, 99, 82, 81, 79  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    ```  
  
2.  <span data-ttu-id="a5bb6-110">Skopiuj następujące wiersze do pliku o nazwie names.csv i zapisać go w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-110">Copy the following lines into a file that is named names.csv and save it to your project folder.</span></span> <span data-ttu-id="a5bb6-111">Arkusz danych zawierający identyfikatora dla użytkowników domowych, imię i nazwisko studenta reprezentuje plik</span><span class="sxs-lookup"><span data-stu-id="a5bb6-111">The file represents a spreadsheet that contains the student's last name, first name, and student ID.</span></span>  
  
    ```  
    Omelchenko,Svetlana,111  
    O'Donnell,Claire,112  
    Mortensen,Sven,113  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Hugo,118  
    Tucker,Lance,119  
    Adams,Terry,120  
    Zabokritski,Eugene,121  
    Tucker,Michael,122  
    ```  
  
## <a name="example"></a><span data-ttu-id="a5bb6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5bb6-112">Example</span></span>  
  
```vb  
Class JoinStrings  
  
    Shared Sub Main()  
  
        ' Join content from spreadsheet files that contain  
        ' related information. names.csv contains the student name  
        ' plus an ID number. scores.csv contains the ID and a   
        ' set of four test scores. The following query joins  
        ' the scores to the student names by using ID as a  
        ' matching key.  
  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Name:    Last[0],       First[1],  ID[2],     Grade Level[3]  
        '          Omelchenko,    Svetlana,  111,       2  
        ' Score:   StudentID[0],  Exam1[1]   Exam2[2],  Exam3[3],  Exam4[4]  
        '          111,           97,        92,        81,        60  
  
        ' This query joins two dissimilar spreadsheets based on common ID value.  
        ' Multiple from clauses are used instead of a join clause  
        ' in order to store results of id.Split.  
        Dim scoreQuery1 = From name In names   
                         Let n = name.Split(New Char() {","})   
                            From id In scores   
                            Let n2 = id.Split(New Char() {","})   
                            Where n(2) = n2(0)   
                            Select n(0) & "," & n(1) & "," & n2(0) & "," & n2(1) & "," &  
                              n2(2) & "," & n2(3)  
  
        ' Pass a query variable to a Sub and execute it there.  
        ' The query itself is unchanged.  
        OutputQueryResults(scoreQuery1, "Merge two spreadsheets:")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)  
  
        Console.WriteLine(System.Environment.NewLine & message)  
        For Each item As String In query  
            Console.WriteLine(item)  
        Next  
        Console.WriteLine(query.Count & " total names in list")  
  
    End Sub  
End Class  
' Output:  
'Merge two spreadsheets:  
'Adams,Terry,120, 99, 82, 81  
'Fakhouri,Fadi,116, 99, 86, 90  
'Feng,Hanying,117, 93, 92, 80  
'Garcia,Cesar,114, 97, 89, 85  
'Garcia,Debra,115, 35, 72, 91  
'Garcia,Hugo,118, 92, 90, 83  
'Mortensen,Sven,113, 88, 94, 65  
'O'Donnell,Claire,112, 75, 84, 91  
'Omelchenko,Svetlana,111, 97, 92, 81  
'Tucker,Lance,119, 68, 79, 88  
'Tucker,Michael,122, 94, 92, 91  
'Zabokritski,Eugene,121, 96, 85, 91  
'12 total names in list  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5bb6-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a5bb6-113">Compiling the Code</span></span>  
 <span data-ttu-id="a5bb6-114">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a5bb6-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5bb6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5bb6-115">See Also</span></span>  
 [<span data-ttu-id="a5bb6-116">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5bb6-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="a5bb6-117">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5bb6-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
