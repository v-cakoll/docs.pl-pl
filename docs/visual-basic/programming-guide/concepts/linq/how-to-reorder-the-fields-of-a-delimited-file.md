---
title: 'Porady: zmienianie kolejności pól w rozdzielonym pliku (LINQ)'
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 736f0218f14f0077683456599d3d7ef3ecec7517
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347602"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="70f11-102">Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f11-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="70f11-103">Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używany do przechowywania danych arkusza kalkulacyjnego lub innych danych tabelarycznych, które są reprezentowane przez wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="70f11-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="70f11-104">Za pomocą metody <xref:System.String.Split%2A>, aby rozdzielić pola, można bardzo łatwo wykonywać zapytania i manipulować plikami CSV przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="70f11-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="70f11-105">W rzeczywistości ta sama technika może służyć do zmiany kolejności części dowolnego strukturalnego wiersza tekstu. nie jest to ograniczone do plików CSV.</span><span class="sxs-lookup"><span data-stu-id="70f11-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>

<span data-ttu-id="70f11-106">W poniższym przykładzie Załóżmy, że trzy kolumny reprezentują uczniów "" nazwisko, "imię i nazwisko" i "ID".</span><span class="sxs-lookup"><span data-stu-id="70f11-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="70f11-107">Pola są w kolejności alfabetycznej na podstawie nazwisk uczniów.</span><span class="sxs-lookup"><span data-stu-id="70f11-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="70f11-108">Zapytanie generuje nową sekwencję, w której zostanie wyświetlona kolumna ID, a po niej druga kolumna łącząca imię i nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="70f11-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="70f11-109">Wiersze są zmieniane proporcjonalnie do pola ID.</span><span class="sxs-lookup"><span data-stu-id="70f11-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="70f11-110">Wyniki są zapisywane w nowym pliku, a oryginalne dane nie są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="70f11-110">The results are saved into a new file and the original data is not modified.</span></span>

### <a name="to-create-the-data-file"></a><span data-ttu-id="70f11-111">Aby utworzyć plik danych</span><span class="sxs-lookup"><span data-stu-id="70f11-111">To create the data file</span></span>

1. <span data-ttu-id="70f11-112">Skopiuj następujące wiersze do zwykłego pliku tekstowego o nazwie spreadsheet1. csv.</span><span class="sxs-lookup"><span data-stu-id="70f11-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="70f11-113">Zapisz plik w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="70f11-113">Save the file in your project folder.</span></span>

    ```csv
    Adams,Terry,120
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Cesar,114
    Garcia,Debra,115
    Garcia,Hugo,118
    Mortensen,Sven,113
    O'Donnell,Claire,112
    Omelchenko,Svetlana,111
    Tucker,Lance,119
    Tucker,Michael,122
    Zabokritski,Eugene,121
    ```

## <a name="example"></a><span data-ttu-id="70f11-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="70f11-114">Example</span></span>

```vb
Class CSVFiles

    Shared Sub Main()

        ' Create the IEnumerable data source.
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")

        ' Execute the query. Put field 2 first, then
        ' reverse and combine fields 0 and 1 from the old field
        Dim lineQuery = From line In lines
                        Let x = line.Split(New Char() {","})
                        Order By x(2)
                        Select x(2) & ", " & (x(1) & " " & x(0))

        ' Execute the query and write out the new file. Note that WriteAllLines
        ' takes a string array, so ToArray is called on the query.
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())

        ' Keep console window open in debug mode.
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output to spreadsheet2.csv:
' 111, Svetlana Omelchenko
' 112, Claire O'Donnell
' 113, Sven Mortensen
' 114, Cesar Garcia
' 115, Debra Garcia
' 116, Fadi Fakhouri
' 117, Hanying Feng
' 118, Hugo Garcia
' 119, Lance Tucker
' 120, Terry Adams
' 121, Eugene Zabokritski
' 122, Michael Tucker
```

## <a name="see-also"></a><span data-ttu-id="70f11-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70f11-115">See also</span></span>

- [<span data-ttu-id="70f11-116">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f11-116">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="70f11-117">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70f11-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="70f11-118">Instrukcje: generowanie kodu XML z plików CSV</span><span class="sxs-lookup"><span data-stu-id="70f11-118">How to: Generate XML from CSV Files</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
