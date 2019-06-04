---
title: Przykład wykonania odroczonego (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: c9ac87cf2b2af4114e5a20c211b4a6b3f7fced6b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486108"
---
# <a name="deferred-execution-example-c"></a>Przykład wykonania odroczonego (C#)
W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie z opóźnieniem wpływa na wykonywanie Twojego zapytaniach składnika LINQ to XML.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kolejność wykonywania, korzystając z metody rozszerzenia, która używa odroczonego wykonania. Przykład deklaruje tablicę trzy ciągi. Następnie wykonuje iterację przez zbiorze zwróconym przez `ConvertCollectionToUpperCase`.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Należy zauważyć, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`, każdy element jest pobierana z tablicy ciągów źródłowych i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.  
  
 Widać, że całej tablicy ciągów nie jest konwertowana na wielkie litery, przetworzenia każdego elementu w kolekcji zwrócone `foreach` pętli w `Main`.  
  
 Następny temat w tym samouczku przedstawiono łańcucha zapytań razem:  
  
- [Przykład łączenia łańcuchowego zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
