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
# <a name="intermediate-materialization-c"></a><span data-ttu-id="75432-102">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="75432-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="75432-103">Jeśli nie jesteś ostrożny, w niektórych sytuacjach można drastycznie zmienić pamięć i profil wydajności aplikacji, powodując przedwczesne materializacji kolekcji w kwerendach.</span><span class="sxs-lookup"><span data-stu-id="75432-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="75432-104">Niektóre standardowe operatory zapytań powodują materializację ich kolekcji źródłowej przed uzyskaniem pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="75432-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="75432-105">Na przykład <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw iteruje za pośrednictwem całej kolekcji źródłowej, a następnie sortuje wszystkie elementy, a następnie w końcu daje pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="75432-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="75432-106">Oznacza to, że uzyskanie pierwszego elementu zamówionej kolekcji jest kosztowne; każdy element później nie jest drogie.</span><span class="sxs-lookup"><span data-stu-id="75432-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="75432-107">Ma to sens: byłoby niemożliwe dla tego operatora kwerendy zrobić inaczej.</span><span class="sxs-lookup"><span data-stu-id="75432-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75432-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="75432-108">Example</span></span>  
 <span data-ttu-id="75432-109">W tym przykładzie zmienia poprzedni przykład.</span><span class="sxs-lookup"><span data-stu-id="75432-109">This example alters the previous example.</span></span> <span data-ttu-id="75432-110">Metoda `AppendString` wywołuje <xref:System.Linq.Enumerable.ToList%2A> przed iteracji za pośrednictwem źródła.</span><span class="sxs-lookup"><span data-stu-id="75432-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="75432-111">Powoduje to materializację.</span><span class="sxs-lookup"><span data-stu-id="75432-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="75432-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="75432-112">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="75432-113">W tym przykładzie widać, że <xref:System.Linq.Enumerable.ToList%2A> wywołanie przyczyn `AppendString` wyliczyć całe źródło przed uzyskaniem pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="75432-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="75432-114">Jeśli źródłem była duża tablica, znacznie zmieniłoby to profil pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75432-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="75432-115">Standardowe operatory zapytań mogą być również połączone ze sobą.</span><span class="sxs-lookup"><span data-stu-id="75432-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="75432-116">Ostatni temat w tym samouczku ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="75432-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="75432-117">Łączenie standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="75432-117">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="75432-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75432-118">See also</span></span>

- [<span data-ttu-id="75432-119">Samouczek: Łączenie zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="75432-119">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
