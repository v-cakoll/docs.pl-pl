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
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="f2ef9-102">Łączenie standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="f2ef9-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="f2ef9-103">Jest to ostatni temat w [samouczku: Łączenie zapytań razem (C#).](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="f2ef9-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="f2ef9-104">Standardowe operatory zapytań mogą być również połączone ze sobą.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="f2ef9-105">Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatora, a także działa w sposób leniwy.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="f2ef9-106">Żadne wyniki pośrednie nie są przez nią zmaterializowane.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2ef9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2ef9-107">Example</span></span>  
 <span data-ttu-id="f2ef9-108">W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> metoda jest `ConvertCollectionToUpperCase`wywoływana przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="f2ef9-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="f2ef9-109">Metoda <xref:System.Linq.Enumerable.Where%2A> działa prawie dokładnie w taki sam sposób, jak metody leniwe `ConvertCollectionToUpperCase` używane `AppendString`w poprzednich przykładach w tym samouczku i .</span><span class="sxs-lookup"><span data-stu-id="f2ef9-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="f2ef9-110">Jedną z różnic jest to, że w tym przypadku <xref:System.Linq.Enumerable.Where%2A> metoda iteruje za pośrednictwem jego kolekcji źródłowej, określa, że pierwszy element nie przekazuje predykatu, a następnie pobiera następny element, który przechodzi.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="f2ef9-111">Następnie daje drugi element.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="f2ef9-112">Jednak podstawowa idea jest taka sama: kolekcje pośrednie nie są zmaterializowane, chyba że muszą być.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="f2ef9-113">Gdy używane są wyrażenia kwerend, są konwertowane na wywołania do standardowych operatorów kwerend i mają zastosowanie te same zasady.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="f2ef9-114">Wszystkie przykłady w tej sekcji, które są kwerendy Office Otwarte dokumenty XML używają tej samej zasady.</span><span class="sxs-lookup"><span data-stu-id="f2ef9-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="f2ef9-115">Odroczone wykonanie i oceny z opóźnieniem są niektóre z podstawowych pojęć, które należy zrozumieć, aby skutecznie używać LINQ (i LINQ do XML).</span><span class="sxs-lookup"><span data-stu-id="f2ef9-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="f2ef9-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f2ef9-116">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
