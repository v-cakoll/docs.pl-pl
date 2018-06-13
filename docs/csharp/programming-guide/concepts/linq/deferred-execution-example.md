---
title: Wykonanie odroczone przykład (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 8613f2335e5b3cb2a012f5309307e081b9400709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335929"
---
# <a name="deferred-execution-example-c"></a>Wykonanie odroczone przykład (C#)
W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie leniwe wpływa na wykonanie programu LINQ do XML zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kolejność wykonywania, korzystając z metody rozszerzenia, który używa odroczonego wykonania. Przykład deklaruje tablicę trzy ciągi. Go następnie iteruje po kolekcji zwróconej przez `ConvertCollectionToUpperCase`.  
  
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
  
 Zwróć uwagę, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`każdego elementu jest pobierana z tablicy ciągów źródła i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.  
  
 Widać, że cała tablica ciągów nie jest przekonwertowany na wielkie litery, przed przetworzeniem każdego elementu w zwracanej kolekcji w `foreach` pętli w `Main`.  
  
 Następnego tematu w tym samouczku przedstawiono razem CBC zapytania:  
  
-   [Tworzenie łańcuchów przykład kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
