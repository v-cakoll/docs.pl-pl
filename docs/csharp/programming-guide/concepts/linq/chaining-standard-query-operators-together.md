---
title: Łączenie standardowych operatorów zapytań razem (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204203"
---
# <a name="chaining-standard-query-operators-together-c"></a>Łączenie standardowych operatorów zapytań razem (C#)
Jest to ostatni temat w [samouczku: Łączenie zapytań razem (C#).](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)  
  
 Standardowe operatory zapytań mogą być również połączone ze sobą. Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatora, a także działa w sposób leniwy. Żadne wyniki pośrednie nie są przez nią zmaterializowane.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> metoda jest `ConvertCollectionToUpperCase`wywoływana przed wywołaniem . Metoda <xref:System.Linq.Enumerable.Where%2A> działa prawie dokładnie w taki sam sposób, jak metody leniwe `ConvertCollectionToUpperCase` używane `AppendString`w poprzednich przykładach w tym samouczku i .  
  
 Jedną z różnic jest to, że w tym przypadku <xref:System.Linq.Enumerable.Where%2A> metoda iteruje za pośrednictwem jego kolekcji źródłowej, określa, że pierwszy element nie przekazuje predykatu, a następnie pobiera następny element, który przechodzi. Następnie daje drugi element.  
  
 Jednak podstawowa idea jest taka sama: kolekcje pośrednie nie są zmaterializowane, chyba że muszą być.  
  
 Gdy używane są wyrażenia kwerend, są konwertowane na wywołania do standardowych operatorów kwerend i mają zastosowanie te same zasady.  
  
 Wszystkie przykłady w tej sekcji, które są kwerendy Office Otwarte dokumenty XML używają tej samej zasady. Odroczone wykonanie i oceny z opóźnieniem są niektóre z podstawowych pojęć, które należy zrozumieć, aby skutecznie używać LINQ (i LINQ do XML).  
  
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
