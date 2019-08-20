---
title: Łączenie standardowych operatorów zapytań (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 89cf7f526bdc60881e901d7ca8f556e97488b220
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594840"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="50195-102">Łączenie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="50195-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="50195-103">Jest to ostatni temat w [samouczku: Łączenie łańcuchowe zapytań (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) — samouczek.</span><span class="sxs-lookup"><span data-stu-id="50195-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="50195-104">Standardowe operatory zapytań można również łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="50195-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="50195-105">Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, a także działa w sposób opóźniony.</span><span class="sxs-lookup"><span data-stu-id="50195-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="50195-106">Żadne wyniki pośrednie nie są dla niego materiałowe.</span><span class="sxs-lookup"><span data-stu-id="50195-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50195-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="50195-107">Example</span></span>  
 <span data-ttu-id="50195-108">W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> Metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="50195-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="50195-109">Metoda działa w prawie dokładnie taki sam sposób, jak metody opóźnione używane w poprzednich przykładach w tym `ConvertCollectionToUpperCase` samouczku `AppendString`i. <xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="50195-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="50195-110">Jedną z różnic jest to, <xref:System.Linq.Enumerable.Where%2A> że w tym przypadku Metoda iteruje za pomocą kolekcji źródłowej, określa, że pierwszy element nie przekazuje predykatu, a następnie pobiera następny element, który jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="50195-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="50195-111">Następnie zwraca drugi element.</span><span class="sxs-lookup"><span data-stu-id="50195-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="50195-112">Jednak podstawowe pomysły są takie same: Kolekcje pośrednie nie są materiałami, chyba że muszą być.</span><span class="sxs-lookup"><span data-stu-id="50195-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="50195-113">Gdy wyrażenia zapytania są używane, są konwertowane na wywołania do standardowych operatorów zapytań i obowiązują te same zasady.</span><span class="sxs-lookup"><span data-stu-id="50195-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="50195-114">Wszystkie przykłady w tej sekcji, które wykonują zapytania o dokumenty w programie Office Open XML, używają tej samej zasady.</span><span class="sxs-lookup"><span data-stu-id="50195-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="50195-115">Wykonywanie odroczone i Ocena z opóźnieniem to niektóre podstawowe koncepcje, które należy zrozumieć, aby skutecznie używać LINQ (i LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="50195-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="50195-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="50195-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  