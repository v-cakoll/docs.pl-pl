---
title: Pośredni materializację (C#)
description: Ten przykład w języku C# przedstawia pośredni materializację, gdzie zapytanie powoduje, że AppendString wyliczyć całe Źródło przed uzyskaniem pierwszego elementu.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165714"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="d88c2-103">Pośredni materializację (C#)</span><span class="sxs-lookup"><span data-stu-id="d88c2-103">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="d88c2-104">Jeśli nie jest to dokładne, w niektórych sytuacjach można radykalnie zmienić profil pamięci i wydajności aplikacji, powodując przedwcześnie materializację kolekcji w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="d88c2-104">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="d88c2-105">Niektóre standardowe operatory zapytań powodują materializację kolekcji źródłowej przed uzyskaniem pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="d88c2-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="d88c2-106">Na przykład program <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw wykonuje iterację w całej kolekcji źródłowej, sortuje wszystkie elementy, a następnie zwraca pierwszy element.</span><span class="sxs-lookup"><span data-stu-id="d88c2-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="d88c2-107">Oznacza to, że jest kosztowne uzyskanie pierwszego elementu kolekcji uporządkowanej; Każdy element nie jest kosztowny.</span><span class="sxs-lookup"><span data-stu-id="d88c2-107">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="d88c2-108">Jest to zrozumiałe: byłoby niemożliwe dla tego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="d88c2-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d88c2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d88c2-109">Example</span></span>  
 <span data-ttu-id="d88c2-110">Ten przykład zmienia poprzedni przykład.</span><span class="sxs-lookup"><span data-stu-id="d88c2-110">This example alters the previous example.</span></span> <span data-ttu-id="d88c2-111">`AppendString`Metoda wywołuje <xref:System.Linq.Enumerable.ToList%2A> przed iteracją w źródle.</span><span class="sxs-lookup"><span data-stu-id="d88c2-111">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="d88c2-112">Powoduje to materializację.</span><span class="sxs-lookup"><span data-stu-id="d88c2-112">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="d88c2-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d88c2-113">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="d88c2-114">W tym przykładzie można zobaczyć, że wywołanie <xref:System.Linq.Enumerable.ToList%2A> powoduje `AppendString` Wyliczenie całego źródła przed uzyskaniem pierwszego elementu.</span><span class="sxs-lookup"><span data-stu-id="d88c2-114">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="d88c2-115">Jeśli źródłem była duża tablica, znacznie zmienia profil pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d88c2-115">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="d88c2-116">Standardowe operatory zapytań można również łączyć ze sobą.</span><span class="sxs-lookup"><span data-stu-id="d88c2-116">Standard query operators can also be chained together.</span></span> <span data-ttu-id="d88c2-117">Ten samouczek ilustruje ostatni temat w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="d88c2-117">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="d88c2-118">Łączenie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="d88c2-118">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="d88c2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d88c2-119">See also</span></span>

- [<span data-ttu-id="d88c2-120">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="d88c2-120">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
