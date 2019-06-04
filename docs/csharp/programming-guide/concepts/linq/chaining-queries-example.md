---
title: Przykład łączenia łańcuchowego zapytań (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 8685db7461a1ce97c7a9c0045ed842fa4ac1a1f6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486194"
---
# <a name="chaining-queries-example-c"></a>Przykład łączenia łańcuchowego zapytań (C#)
W tym przykładzie opiera się na poprzednim przykładzie i pokazuje, co się stanie po użytkownik łańcucha ze sobą dwa zapytania, oba Użyj wykonanie odroczone i obliczanie z opóźnieniem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wprowadzono inną metodę rozszerzenia, `AppendString`, który dołącza określony ciąg na każdy ciąg znaków w kolekcji źródłowej, a następnie daje nowych parametrów.  
  
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
  
```  
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
  
 W tym przykładzie widać, że każda metoda rozszerzenia działa jedną na raz dla każdego elementu w kolekcji źródłowej.  
  
 Czymś co powinno być jasne, w tym przykładzie jest, mimo że firma Microsoft ma połączone zapytań, które kolekcje, żadne kolekcje pośrednie są zmaterializowany. Zamiast tego każdy element jest przekazywany z jednej metody z opóźnieniem do następnego. Powoduje to dużo mniejsze zużycie pamięci niż podejście, które będą najpierw wykonać jedną tablicę ciągów, a następnie utwórz drugi tablicę ciągów, która został przekonwertowany na wielkie litery, a na koniec Utwórz trzeci tablicę ciągów, w którym każdy ciąg ma wykrzyknika Wskazuje dołączone do niego.  
  
 Następny temat w tym samouczku przedstawiono materializacja pośrednia:  
  
- [Materializacja pośrednia (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
