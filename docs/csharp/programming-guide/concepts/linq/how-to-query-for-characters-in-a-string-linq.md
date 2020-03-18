---
title: Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345680"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)
Ponieważ <xref:System.String> klasa implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny, każdy ciąg można zbadać jako sekwencję znaków. Jednak nie jest to powszechne zastosowanie LINQ. W przypadku operacji dopasowywania wzorców złożonych należy użyć <xref:System.Text.RegularExpressions.Regex> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kwerendy ciąg, aby określić liczbę cyfr, które zawiera. Należy zauważyć, że kwerenda jest "ponownie używane" po wykonaniu po raz pierwszy. Jest to możliwe, ponieważ sama kwerenda nie przechowuje żadnych rzeczywistych wyników.  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (C#)](./linq-and-strings.md)
- [Jak połączyć zapytania LINQ z wyrażeniami regularnymi (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)
