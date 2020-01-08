---
title: Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: e869d57c413d175c092cdc15a6fe54cab94e04b8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347351"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)
Poniższy przykład pokazuje, jak sortować wiersze tekstu strukturalnego, takie jak wartości rozdzielane przecinkami, według dowolnego pola w wierszu. Pole może być określane dynamicznie w czasie wykonywania. Załóżmy, że pola w pliku Scores. csv reprezentują numer IDENTYFIKACYJNy studenta, a następnie serię czterech wyników testu.  
  
### <a name="to-create-a-file-that-contains-data"></a>Aby utworzyć plik zawierający dane  
  
1. Skopiuj dane Score. CSV z tematu [jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) i zapisać je w folderze rozwiązania.  
  
## <a name="example"></a>Przykład  
  
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
  
 W tym przykładzie pokazano również, jak zwrócić zmienną zapytania z metody.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](./linq-and-strings.md)
