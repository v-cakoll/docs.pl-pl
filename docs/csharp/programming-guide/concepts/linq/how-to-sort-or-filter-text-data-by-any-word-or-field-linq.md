---
title: 'Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: dc541d7cc8a4fb5978fb2ed9cc43a548e8f8b253
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320196"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="f8443-102">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f8443-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="f8443-103">Poniższy przykład przedstawia sposób sortowania wierszy tekstu strukturalnych, takich jak wartości rozdzielanych przecinkami, przez którekolwiek z pól w wierszu.</span><span class="sxs-lookup"><span data-stu-id="f8443-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="f8443-104">Pole może być określana dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8443-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="f8443-105">Załóżmy, że pola scores.csv reprezentują numer identyfikacyjny Studenta, następuje szereg cztery wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="f8443-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="f8443-106">Aby utworzyć plik, który zawiera dane</span><span class="sxs-lookup"><span data-stu-id="f8443-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="f8443-107">Kopiowanie danych scores.csv z tematu [porady: Dołącz zawartości z plikami niepodobnych (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) i zapisać ją w folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f8443-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8443-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8443-108">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="f8443-109">W tym przykładzie przedstawiono również sposób zwracania zmiennej zapytania z metody.</span><span class="sxs-lookup"><span data-stu-id="f8443-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8443-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f8443-110">Compiling the Code</span></span>  
 <span data-ttu-id="f8443-111">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="f8443-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8443-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8443-112">See Also</span></span>  
 [<span data-ttu-id="f8443-113">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="f8443-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
