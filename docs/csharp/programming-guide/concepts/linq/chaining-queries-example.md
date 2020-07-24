---
title: Przykład łańcucha zapytań (C#)
description: Ten przykład pokazuje, co się dzieje w przypadku łączenia dwóch zapytań, które używają odroczonego wykonania i oceny z opóźnieniem w języku C#.
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105537"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="a5d96-103">Przykład łańcucha zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="a5d96-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="a5d96-104">Ten przykład kompiluje się w poprzednim przykładzie i pokazuje, co się dzieje w przypadku łączenia dwóch zapytań, które używają odroczonego wykonania i oceny z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="a5d96-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5d96-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5d96-105">Example</span></span>  
 <span data-ttu-id="a5d96-106">W tym przykładzie wprowadzono inną metodę rozszerzenia, `AppendString` która dołącza określony ciąg do każdego ciągu w kolekcji źródłowej, a następnie generuje nowe ciągi.</span><span class="sxs-lookup"><span data-stu-id="a5d96-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="a5d96-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a5d96-107">This example produces the following output:</span></span>  
  
```output  
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
  
 <span data-ttu-id="a5d96-108">W tym przykładzie można zobaczyć, że każda metoda rozszerzająca działa pojedynczo dla każdego elementu w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="a5d96-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="a5d96-109">Co powinno być jasne z tego przykładu, chociaż istnieją łańcuchowe zapytania, które przesyłają kolekcje, a żadne kolekcje pośrednie nie są przeznaczone do materiałów.</span><span class="sxs-lookup"><span data-stu-id="a5d96-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="a5d96-110">Zamiast tego każdy element jest przesyłany z jednej metody opóźnionej do następnej.</span><span class="sxs-lookup"><span data-stu-id="a5d96-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="a5d96-111">Powoduje to znacznie mniejszą ilość pamięci niż podejście, które najpierw przyjmuje jedną tablicę ciągów, a następnie tworzy drugą tablicę ciągów, które zostały przekonwertowane na wielkie litery, i na koniec tworzy trzecią tablicę ciągów, w których każdy ciąg ma do niej dołączony wykrzyknik.</span><span class="sxs-lookup"><span data-stu-id="a5d96-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="a5d96-112">W następnym temacie w tym samouczku przedstawiono materializację pośredni:</span><span class="sxs-lookup"><span data-stu-id="a5d96-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="a5d96-113">Pośredni materializację (C#)</span><span class="sxs-lookup"><span data-stu-id="a5d96-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5d96-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5d96-114">See also</span></span>

- [<span data-ttu-id="a5d96-115">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="a5d96-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
