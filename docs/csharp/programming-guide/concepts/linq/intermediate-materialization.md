---
title: Materializacja pośrednia (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 56c4bb57a931362b3e14f6a8da917ae6907565d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516546"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="5b5f0-102">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="5b5f0-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="5b5f0-103">Jeśli nie jesteś zachować ostrożność, w niektórych sytuacjach można znacząco zmienić profil pamięć i wydajność aplikacji, powodując przedwczesne materializacja kolekcji w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="5b5f0-104">Niektóre standardowe operatory zapytań spowodować materializacja ich kolekcji źródłowej przed reaguje pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="5b5f0-105">Na przykład <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw wykonuje iterację przez jego kolekcja całą źródłową, a następnie sortuje wszystkie elementy i wreszcie zwraca pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="5b5f0-106">To oznacza, że jest kosztowne uzyskać pierwszy element uporządkowaną kolekcję; Każdy element nie jest później kosztowne.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="5b5f0-107">Jest to logiczne: byłoby niemożliwe dla tego operatora zapytania robić.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b5f0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b5f0-108">Example</span></span>  
 <span data-ttu-id="5b5f0-109">Ten przykład modyfikuje poprzedni przykład.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-109">This example alters the previous example.</span></span> <span data-ttu-id="5b5f0-110">`AppendString` Wywołania metody <xref:System.Linq.Enumerable.ToList%2A> przed iteracji w źródle.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="5b5f0-111">Powoduje to materializacja.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="5b5f0-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5b5f0-112">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="5b5f0-113">W tym przykładzie możesz zobaczyć, że wywołanie <xref:System.Linq.Enumerable.ToList%2A> powoduje, że `AppendString` wyliczyć całego źródła przed reaguje na pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="5b5f0-114">Źródło, gdyby dużą tablicę, znacznie zmieniłaby ten profil pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="5b5f0-115">Standardowe operatory zapytań można również łączyć w łańcuch.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="5b5f0-116">Ostatnim temacie w tym samouczku przedstawiono to.</span><span class="sxs-lookup"><span data-stu-id="5b5f0-116">The final topic in this tutorial illustrates this.</span></span>  
  
-   [<span data-ttu-id="5b5f0-117">Łańcucha standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="5b5f0-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b5f0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b5f0-118">See Also</span></span>

- [<span data-ttu-id="5b5f0-119">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="5b5f0-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
