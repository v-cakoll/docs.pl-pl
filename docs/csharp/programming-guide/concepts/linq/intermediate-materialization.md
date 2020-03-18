---
title: Materializacja pośrednia (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253162"
---
# <a name="intermediate-materialization-c"></a>Materializacja pośrednia (C#)
Jeśli nie jesteś ostrożny, w niektórych sytuacjach można drastycznie zmienić pamięć i profil wydajności aplikacji, powodując przedwczesne materializacji kolekcji w kwerendach. Niektóre standardowe operatory zapytań powodują materializację ich kolekcji źródłowej przed uzyskaniem pojedynczego elementu. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw iteruje za pośrednictwem całej kolekcji źródłowej, a następnie sortuje wszystkie elementy, a następnie w końcu daje pierwszy element. Oznacza to, że uzyskanie pierwszego elementu zamówionej kolekcji jest kosztowne; każdy element później nie jest drogie. Ma to sens: byłoby niemożliwe dla tego operatora kwerendy zrobić inaczej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zmienia poprzedni przykład. Metoda `AppendString` wywołuje <xref:System.Linq.Enumerable.ToList%2A> przed iteracji za pośrednictwem źródła. Powoduje to materializację.  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 W tym przykładzie widać, że <xref:System.Linq.Enumerable.ToList%2A> wywołanie przyczyn `AppendString` wyliczyć całe źródło przed uzyskaniem pierwszego elementu. Jeśli źródłem była duża tablica, znacznie zmieniłoby to profil pamięci aplikacji.  
  
 Standardowe operatory zapytań mogą być również połączone ze sobą. Ostatni temat w tym samouczku ilustruje to.  
  
- [Łączenie standardowych operatorów zapytań razem (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Łączenie zapytań razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
