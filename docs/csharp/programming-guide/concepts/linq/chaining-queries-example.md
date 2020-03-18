---
title: Przykład kwerend łańcuchowych (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205416"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="02373-102">Przykład kwerend łańcuchowych (C#)</span><span class="sxs-lookup"><span data-stu-id="02373-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="02373-103">W tym przykładzie opiera się na poprzednim przykładzie i pokazuje, co się dzieje, gdy łańcuch razem dwa zapytania, które używają odroczonego wykonania i oceny z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="02373-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02373-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="02373-104">Example</span></span>  
 <span data-ttu-id="02373-105">W tym przykładzie wprowadzono inną `AppendString`metodę rozszerzenia, która dołącza określony ciąg do każdego ciągu w kolekcji źródłowej, a następnie daje nowe ciągi.</span><span class="sxs-lookup"><span data-stu-id="02373-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="02373-106">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="02373-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="02373-107">W tym przykładzie widać, że każda metoda rozszerzenia działa po jednym na raz dla każdego elementu w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="02373-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="02373-108">Co powinno być jasne z tego przykładu jest to, że mimo że mamy połączone ze sobą zapytania, które dają kolekcje, nie kolekcje pośrednie są zmaterializowane.</span><span class="sxs-lookup"><span data-stu-id="02373-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="02373-109">Zamiast tego każdy element jest przekazywany z jednej metody z opóźnieniem do następnego.</span><span class="sxs-lookup"><span data-stu-id="02373-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="02373-110">Powoduje to znacznie mniejszy ślad pamięci niż podejście, które najpierw zajmie jedną tablicę ciągów, a następnie utworzyć drugą tablicę ciągów, które zostały przekonwertowane na wielkie litery, a na koniec utworzyć trzecią tablicę ciągów, gdzie każdy ciąg ma wykrzyknik do łączonych do niego punktów.</span><span class="sxs-lookup"><span data-stu-id="02373-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="02373-111">Następny temat w tym samouczku ilustruje pośrednią materializację:</span><span class="sxs-lookup"><span data-stu-id="02373-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="02373-112">Materializacja pośrednia (C#)</span><span class="sxs-lookup"><span data-stu-id="02373-112">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="02373-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02373-113">See also</span></span>

- [<span data-ttu-id="02373-114">Samouczek: Łączenie zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="02373-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
