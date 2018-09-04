---
title: Przykład wykonania odroczonego (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0ad1ed2998cfbd612f7f2b60a0d15c7ffcef0daf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518478"
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
  
-   [Przykład łączenia łańcuchowego zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
