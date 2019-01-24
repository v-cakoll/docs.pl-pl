---
title: Materializacja pośrednia (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 065a7e0ffadaa48d400d4f4e3e045014b3658213
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686013"
---
# <a name="intermediate-materialization-c"></a>Materializacja pośrednia (C#)
Jeśli nie jesteś zachować ostrożność, w niektórych sytuacjach można znacząco zmienić profil pamięć i wydajność aplikacji, powodując przedwczesne materializacja kolekcji w zapytaniach. Niektóre standardowe operatory zapytań spowodować materializacja ich kolekcji źródłowej przed reaguje pojedynczy element. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw wykonuje iterację przez jego kolekcja całą źródłową, a następnie sortuje wszystkie elementy i wreszcie zwraca pierwszy element. To oznacza, że jest kosztowne uzyskać pierwszy element uporządkowaną kolekcję; Każdy element nie jest później kosztowne. Jest to logiczne: Nie można wysyłać dla tego operatora zapytania robić.  
  
## <a name="example"></a>Przykład  
 Ten przykład modyfikuje poprzedni przykład. `AppendString` Wywołania metody <xref:System.Linq.Enumerable.ToList%2A> przed iteracji w źródle. Powoduje to materializacja.  
  
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
  
```  
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
  
 W tym przykładzie możesz zobaczyć, że wywołanie <xref:System.Linq.Enumerable.ToList%2A> powoduje, że `AppendString` wyliczyć całego źródła przed reaguje na pierwszy element. Źródło, gdyby dużą tablicę, znacznie zmieniłaby ten profil pamięci aplikacji.  
  
 Standardowe operatory zapytań można również łączyć w łańcuch. Ostatnim temacie w tym samouczku przedstawiono to.  
  
-   [Łańcucha standardowych operatorów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
