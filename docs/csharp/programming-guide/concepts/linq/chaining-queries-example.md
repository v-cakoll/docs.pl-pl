---
title: Tworzenie łańcuchów przykład kwerendy (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: d28f5f4ed4f9e6deb5f6f3d381d310ebcef6e132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327695"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="7e1f9-102">Tworzenie łańcuchów przykład kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="7e1f9-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="7e1f9-103">W tym przykładzie jest oparty na poprzednim przykładzie i pokazuje, co się stanie w przypadku łańcucha ze sobą dwie kwerendę dotyczącą zarówno Użyj odroczonego wykonania i obliczanie leniwe.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e1f9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e1f9-104">Example</span></span>  
 <span data-ttu-id="7e1f9-105">W tym przykładzie wprowadzono inną metodę rozszerzenia, `AppendString`, które dołącza określony ciąg na ciąg, co w kolekcji źródłowej, a następnie daje nowych ciągów.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="7e1f9-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7e1f9-106">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="7e1f9-107">W tym przykładzie widać, że każda metoda rozszerzenia działa jeden z nich, dla każdego elementu w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="7e1f9-108">Co powinno być wolne w tym przykładzie jest, mimo że firma Microsoft ma połączone zapytań, które zwracają kolekcje, żadne kolekcje pośredniego jest zmaterializowany.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="7e1f9-109">Zamiast tego każdy element jest przekazywany z jedną metodę opóźnieniem do następnego.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="7e1f9-110">Powoduje to mniejsze zużycie pamięci, niż metody, które będzie najpierw wykonać jedną tablicą ciągów, a następnie utworzyć drugi tablicy ciągów, który został przekonwertowany na wielkie litery, a na koniec Utwórz trzeci tablicy ciągów, gdzie każdy ciąg ma wykrzyknika punkty dołączone do niego.</span><span class="sxs-lookup"><span data-stu-id="7e1f9-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="7e1f9-111">Następnego tematu w tym samouczku przedstawiono materialization pośredniego:</span><span class="sxs-lookup"><span data-stu-id="7e1f9-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
-   [<span data-ttu-id="7e1f9-112">Pośredni Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="7e1f9-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e1f9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e1f9-113">See Also</span></span>  
 [<span data-ttu-id="7e1f9-114">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="7e1f9-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
