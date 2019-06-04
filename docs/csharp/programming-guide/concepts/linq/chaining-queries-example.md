---
title: Przykład łączenia łańcuchowego zapytań (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 8685db7461a1ce97c7a9c0045ed842fa4ac1a1f6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486194"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="0fee3-102">Przykład łączenia łańcuchowego zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="0fee3-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="0fee3-103">W tym przykładzie opiera się na poprzednim przykładzie i pokazuje, co się stanie po użytkownik łańcucha ze sobą dwa zapytania, oba Użyj wykonanie odroczone i obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="0fee3-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fee3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fee3-104">Example</span></span>  
 <span data-ttu-id="0fee3-105">W tym przykładzie wprowadzono inną metodę rozszerzenia, `AppendString`, który dołącza określony ciąg na każdy ciąg znaków w kolekcji źródłowej, a następnie daje nowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="0fee3-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="0fee3-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0fee3-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="0fee3-107">W tym przykładzie widać, że każda metoda rozszerzenia działa jedną na raz dla każdego elementu w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="0fee3-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="0fee3-108">Czymś co powinno być jasne, w tym przykładzie jest, mimo że firma Microsoft ma połączone zapytań, które kolekcje, żadne kolekcje pośrednie są zmaterializowany.</span><span class="sxs-lookup"><span data-stu-id="0fee3-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="0fee3-109">Zamiast tego każdy element jest przekazywany z jednej metody z opóźnieniem do następnego.</span><span class="sxs-lookup"><span data-stu-id="0fee3-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="0fee3-110">Powoduje to dużo mniejsze zużycie pamięci niż podejście, które będą najpierw wykonać jedną tablicę ciągów, a następnie utwórz drugi tablicę ciągów, która został przekonwertowany na wielkie litery, a na koniec Utwórz trzeci tablicę ciągów, w którym każdy ciąg ma wykrzyknika Wskazuje dołączone do niego.</span><span class="sxs-lookup"><span data-stu-id="0fee3-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="0fee3-111">Następny temat w tym samouczku przedstawiono materializacja pośrednia:</span><span class="sxs-lookup"><span data-stu-id="0fee3-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="0fee3-112">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="0fee3-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="0fee3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fee3-113">See also</span></span>

- [<span data-ttu-id="0fee3-114">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="0fee3-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
