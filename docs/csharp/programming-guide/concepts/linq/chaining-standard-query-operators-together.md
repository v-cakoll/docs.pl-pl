---
title: Łączenie standardowych operatorów zapytań (C#)
description: Ten przykład pokazuje, jak standardowe operatory zapytań można również łączyć ze sobą w języku C#. Zapytanie nie zmaterializowania wyników pośrednich.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104072"
---
# <a name="chaining-standard-query-operators-together-c"></a>Łączenie standardowych operatorów zapytań (C#)
Jest to ostatni temat w [samouczku: Tworzenie łańcucha kwerend razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) samouczek.  
  
 Standardowe operatory zapytań można również łączyć ze sobą. Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, a także działa w sposób opóźniony. Żadne wyniki pośrednie nie są dla niego materiałowe.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> Metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase` . <xref:System.Linq.Enumerable.Where%2A>Metoda działa w prawie dokładnie taki sam sposób, jak metody opóźnione używane w poprzednich przykładach w tym samouczku `ConvertCollectionToUpperCase` i `AppendString` .  
  
 Jedną z różnic jest to, że w tym przypadku <xref:System.Linq.Enumerable.Where%2A> Metoda iteruje za pomocą kolekcji źródłowej, określa, że pierwszy element nie przekazuje predykatu, a następnie pobiera następny element, który jest przekazywany. Następnie zwraca drugi element.  
  
 Jednak podstawowe pomysły są takie same: Kolekcje pośrednie nie są oznaczane materiałami, chyba że muszą być.  
  
 Gdy wyrażenia zapytania są używane, są konwertowane na wywołania do standardowych operatorów zapytań i obowiązują te same zasady.  
  
 Wszystkie przykłady w tej sekcji, które wykonują zapytania o dokumenty w programie Office Open XML, używają tej samej zasady. Wykonywanie odroczone i Ocena z opóźnieniem to niektóre podstawowe koncepcje, które należy zrozumieć, aby skutecznie używać LINQ (i LINQ to XML).  
  
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
            where s.CompareTo("D") >= 0  
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
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
