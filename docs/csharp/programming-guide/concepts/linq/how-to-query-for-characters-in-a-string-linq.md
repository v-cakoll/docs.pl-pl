---
title: Jak wykonać zapytanie o znaki w ciągu (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345680"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Jak wykonać zapytanie o znaki w ciągu (LINQ) (C#)
Ponieważ Klasa <xref:System.String> implementuje ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601>, każdy ciąg może być badany jako sekwencja znaków. Nie jest to jednak powszechne użycie LINQ. W przypadku złożonych operacji dopasowania do wzorca Użyj klasy <xref:System.Text.RegularExpressions.Regex>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do ciągu, aby określić liczbę cyfr, które zawiera. Należy pamiętać, że zapytanie jest "ponownie używane" po raz pierwszy. Jest to możliwe, ponieważ samo zapytanie nie przechowuje żadnych rzeczywistych wyników.  
  
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
 Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. Linq i system.IO.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](./linq-and-strings.md)
- [Jak połączyć zapytania LINQ z wyrażeniami regularnymiC#()](./how-to-combine-linq-queries-with-regular-expressions.md)
