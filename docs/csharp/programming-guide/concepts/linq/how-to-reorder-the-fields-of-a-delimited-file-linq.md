---
title: 'Instrukcje: Zmień kolejność pól rozdzielanego pliku (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 31cb7b936f58653e6223501f3b03cd9472b92453
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253459"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="da89a-102">Instrukcje: Zmień kolejność pól rozdzielanego pliku (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="da89a-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="da89a-103">Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używany do przechowywania danych arkusza kalkulacyjnego lub innych danych tabelarycznych, które są reprezentowane przez wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="da89a-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="da89a-104">Za pomocą <xref:System.String.Split%2A> metody do rozdzielania pól, można bardzo łatwo wysyłać zapytania do plików CSV i manipulować nimi przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="da89a-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="da89a-105">W rzeczywistości ta sama technika może służyć do zmiany kolejności części dowolnego strukturalnego wiersza tekstu. nie jest to ograniczone do plików CSV.</span><span class="sxs-lookup"><span data-stu-id="da89a-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="da89a-106">W poniższym przykładzie Załóżmy, że trzy kolumny reprezentują uczniów "" nazwisko, "imię i nazwisko" i "ID".</span><span class="sxs-lookup"><span data-stu-id="da89a-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="da89a-107">Pola są w kolejności alfabetycznej na podstawie nazwisk uczniów.</span><span class="sxs-lookup"><span data-stu-id="da89a-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="da89a-108">Zapytanie generuje nową sekwencję, w której zostanie wyświetlona kolumna ID, a po niej druga kolumna łącząca imię i nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="da89a-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="da89a-109">Wiersze są zmieniane proporcjonalnie do pola ID.</span><span class="sxs-lookup"><span data-stu-id="da89a-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="da89a-110">Wyniki są zapisywane w nowym pliku, a oryginalne dane nie są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="da89a-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="da89a-111">Aby utworzyć plik danych</span><span class="sxs-lookup"><span data-stu-id="da89a-111">To create the data file</span></span>  
  
1. <span data-ttu-id="da89a-112">Skopiuj następujące wiersze do zwykłego pliku tekstowego o nazwie spreadsheet1. csv.</span><span class="sxs-lookup"><span data-stu-id="da89a-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="da89a-113">Zapisz plik w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="da89a-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="da89a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="da89a-114">Example</span></span>  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da89a-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="da89a-115">Compiling the Code</span></span>  
<span data-ttu-id="da89a-116">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="da89a-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="da89a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da89a-117">See also</span></span>

- [<span data-ttu-id="da89a-118">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="da89a-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="da89a-119">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="da89a-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="da89a-120">Instrukcje: Generuj XML z plików CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="da89a-120">How to: Generate XML from CSV Files (C#)</span></span>](./how-to-generate-xml-from-csv-files.md)
