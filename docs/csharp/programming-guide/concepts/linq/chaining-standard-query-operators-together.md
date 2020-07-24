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
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="758ac-104">Łączenie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="758ac-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="758ac-105">Jest to ostatni temat w [samouczku: Tworzenie łańcucha kwerend razem (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) samouczek.</span><span class="sxs-lookup"><span data-stu-id="758ac-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="758ac-106">Standardowe operatory zapytań można również łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="758ac-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="758ac-107">Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, a także działa w sposób opóźniony.</span><span class="sxs-lookup"><span data-stu-id="758ac-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="758ac-108">Żadne wyniki pośrednie nie są dla niego materiałowe.</span><span class="sxs-lookup"><span data-stu-id="758ac-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="758ac-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="758ac-109">Example</span></span>  
 <span data-ttu-id="758ac-110">W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> Metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="758ac-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="758ac-111"><xref:System.Linq.Enumerable.Where%2A>Metoda działa w prawie dokładnie taki sam sposób, jak metody opóźnione używane w poprzednich przykładach w tym samouczku `ConvertCollectionToUpperCase` i `AppendString` .</span><span class="sxs-lookup"><span data-stu-id="758ac-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="758ac-112">Jedną z różnic jest to, że w tym przypadku <xref:System.Linq.Enumerable.Where%2A> Metoda iteruje za pomocą kolekcji źródłowej, określa, że pierwszy element nie przekazuje predykatu, a następnie pobiera następny element, który jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="758ac-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="758ac-113">Następnie zwraca drugi element.</span><span class="sxs-lookup"><span data-stu-id="758ac-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="758ac-114">Jednak podstawowe pomysły są takie same: Kolekcje pośrednie nie są oznaczane materiałami, chyba że muszą być.</span><span class="sxs-lookup"><span data-stu-id="758ac-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="758ac-115">Gdy wyrażenia zapytania są używane, są konwertowane na wywołania do standardowych operatorów zapytań i obowiązują te same zasady.</span><span class="sxs-lookup"><span data-stu-id="758ac-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="758ac-116">Wszystkie przykłady w tej sekcji, które wykonują zapytania o dokumenty w programie Office Open XML, używają tej samej zasady.</span><span class="sxs-lookup"><span data-stu-id="758ac-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="758ac-117">Wykonywanie odroczone i Ocena z opóźnieniem to niektóre podstawowe koncepcje, które należy zrozumieć, aby skutecznie używać LINQ (i LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="758ac-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="758ac-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="758ac-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
