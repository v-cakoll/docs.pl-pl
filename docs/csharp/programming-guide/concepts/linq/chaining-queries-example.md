---
title: Przykład łańcucha kwerend (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205416"
---
# <a name="chaining-queries-example-c"></a>Przykład łańcucha kwerend (C#)
Ten przykład kompiluje się w poprzednim przykładzie i pokazuje, co się dzieje w przypadku łączenia dwóch zapytań, które używają odroczonego wykonania i oceny z opóźnieniem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wprowadzono `AppendString`inną metodę rozszerzenia, która dołącza określony ciąg do każdego ciągu w kolekcji źródłowej, a następnie generuje nowe ciągi.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 W tym przykładzie można zobaczyć, że każda metoda rozszerzająca działa pojedynczo dla każdego elementu w kolekcji źródłowej.  
  
 Co powinno być jasne z tego przykładu, chociaż istnieją łańcuchowe zapytania, które przesyłają kolekcje, a żadne kolekcje pośrednie nie są przeznaczone do materiałów. Zamiast tego każdy element jest przesyłany z jednej metody opóźnionej do następnej. Powoduje to znacznie mniejszą ilość pamięci niż podejście, które najpierw przyjmuje jedną tablicę ciągów, a następnie tworzy drugą tablicę ciągów, które zostały przekonwertowane na wielkie litery, i na koniec tworzy trzecią tablicę ciągów, w których każdy ciąg ma wykrzyknik dołączone punkty.  
  
 W następnym temacie w tym samouczku przedstawiono materializację pośredni:  
  
- [Pośredni materializację (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
