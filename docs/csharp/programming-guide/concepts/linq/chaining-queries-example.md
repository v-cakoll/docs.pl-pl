---
title: Przykład kwerend łańcuchowych (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205416"
---
# <a name="chaining-queries-example-c"></a>Przykład kwerend łańcuchowych (C#)
W tym przykładzie opiera się na poprzednim przykładzie i pokazuje, co się dzieje, gdy łańcuch razem dwa zapytania, które używają odroczonego wykonania i oceny z opóźnieniem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wprowadzono inną `AppendString`metodę rozszerzenia, która dołącza określony ciąg do każdego ciągu w kolekcji źródłowej, a następnie daje nowe ciągi.  
  
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
  
 W tym przykładzie widać, że każda metoda rozszerzenia działa po jednym na raz dla każdego elementu w kolekcji źródłowej.  
  
 Co powinno być jasne z tego przykładu jest to, że mimo że mamy połączone ze sobą zapytania, które dają kolekcje, nie kolekcje pośrednie są zmaterializowane. Zamiast tego każdy element jest przekazywany z jednej metody z opóźnieniem do następnego. Powoduje to znacznie mniejszy ślad pamięci niż podejście, które najpierw zajmie jedną tablicę ciągów, a następnie utworzyć drugą tablicę ciągów, które zostały przekonwertowane na wielkie litery, a na koniec utworzyć trzecią tablicę ciągów, gdzie każdy ciąg ma wykrzyknik do łączonych do niego punktów.  
  
 Następny temat w tym samouczku ilustruje pośrednią materializację:  
  
- [Materializacja pośrednia (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Łączenie zapytań razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
