---
title: 'Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: ff8782571bccabe17e9c01331339cf729ff6620a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314987"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="42e41-102">Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="42e41-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="42e41-103">Plik wartości rozdzielanych przecinkami (CSV) to plik tekstowy, który jest często używana do przechowywania danych w arkuszu kalkulacyjnym lub inne dane tabelaryczne, który jest reprezentowany przez wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="42e41-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="42e41-104">Za pomocą <xref:System.String.Split%2A> metodę, aby rozdzielić pola, jest bardzo proste w celu wykonywania zapytań i manipulowania plików CSV za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="42e41-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="42e41-105">W rzeczywistości tej samej techniki można zmieniać kolejność części ze strukturą wiersza tekstu. nie jest ograniczona do plików CSV.</span><span class="sxs-lookup"><span data-stu-id="42e41-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="42e41-106">W poniższym przykładzie przyjęto założenie, że trzy kolumny reprezentują studentów "last name," "imię" i "identyfikator".</span><span class="sxs-lookup"><span data-stu-id="42e41-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="42e41-107">Pola są w kolejności alfabetycznej, w oparciu o nazwiska uczniów.</span><span class="sxs-lookup"><span data-stu-id="42e41-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="42e41-108">Zapytanie tworzy nową sekwencję, w której kolumna Identyfikatora pojawiają się pierwsze, następuje drugiej kolumny, która łączy imię i Nazwisko ucznia.</span><span class="sxs-lookup"><span data-stu-id="42e41-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="42e41-109">Wiersze zostaną ponownie uporządkowane według pola identyfikator.</span><span class="sxs-lookup"><span data-stu-id="42e41-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="42e41-110">Wyniki są zapisywane do nowego pliku i oryginalnych danych nie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="42e41-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="42e41-111">Aby utworzyć plik danych</span><span class="sxs-lookup"><span data-stu-id="42e41-111">To create the data file</span></span>  
  
1. <span data-ttu-id="42e41-112">Skopiuj następujące wiersze do zwykły plik tekstowy o nazwie spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="42e41-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="42e41-113">Zapisz plik w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="42e41-113">Save the file in your project folder.</span></span>  
  
    ```  
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
  
## <a name="example"></a><span data-ttu-id="42e41-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="42e41-114">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="42e41-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="42e41-115">Compiling the Code</span></span>  
 <span data-ttu-id="42e41-116">Utwórz projekt, który jest przeznaczony dla .NET Framework w wersji 3.5 lub nowszego, za pomocą odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="42e41-116">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e41-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42e41-117">See also</span></span>

- [<span data-ttu-id="42e41-118">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="42e41-118">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="42e41-119">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="42e41-119">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="42e41-120">Instrukcje: Generowanie kodu XML z plików CSV (C#)</span><span class="sxs-lookup"><span data-stu-id="42e41-120">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
