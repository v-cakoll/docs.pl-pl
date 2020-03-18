---
title: Przykład odroczonego wykonania (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204135"
---
# <a name="deferred-execution-example-c"></a>Przykład odroczonego wykonania (C#)
W tym temacie pokazano, jak odroczone wykonanie i leniwa ocena wpływa na wykonywanie linq do zapytań XML.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kolejność wykonywania przy użyciu metody rozszerzenia, która używa odroczonego wykonania. W przykładzie deklaruje tablicy trzech ciągów. Następnie iteruje przez kolekcję `ConvertCollectionToUpperCase`zwróconą przez .  
  
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
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Należy zauważyć, że podczas iteracji `ConvertCollectionToUpperCase`za pośrednictwem kolekcji zwracanej przez , każdy element jest pobierany z tablicy ciągu źródłowego i konwertowane na wielkie litery przed następnym elementem jest pobierana z tablicy ciągów źródłowych.  
  
 Widać, że cała tablica ciągów nie jest konwertowana na wielkie litery, zanim `foreach` każdy `Main`element w zwróconej kolekcji jest przetwarzany w pętli w .  
  
 Następny temat w tym samouczku ilustruje łączenie zapytań razem:  
  
- [Przykład kwerend łańcuchowych (C#)](./chaining-queries-example.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Łączenie zapytań razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
