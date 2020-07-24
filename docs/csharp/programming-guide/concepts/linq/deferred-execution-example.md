---
title: Przykład wykonania odroczonego (C#)
description: Zobacz, jak odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML w języku C#.
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 65ba4cc150f2fc9d8f44aee352987ea0eeaab0a5
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103948"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="30f53-103">Przykład wykonania odroczonego (C#)</span><span class="sxs-lookup"><span data-stu-id="30f53-103">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="30f53-104">W tym temacie pokazano, w jaki sposób odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="30f53-104">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f53-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="30f53-105">Example</span></span>  
 <span data-ttu-id="30f53-106">Poniższy przykład pokazuje kolejność wykonywania przy użyciu metody rozszerzenia, która korzysta z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="30f53-106">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="30f53-107">Przykład deklaruje tablicę trzech ciągów.</span><span class="sxs-lookup"><span data-stu-id="30f53-107">The example declares an array of three strings.</span></span> <span data-ttu-id="30f53-108">Następnie wykonuje iterację w kolekcji zwróconej przez `ConvertCollectionToUpperCase` .</span><span class="sxs-lookup"><span data-stu-id="30f53-108">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="30f53-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="30f53-109">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="30f53-110">Należy zauważyć, że podczas iteracji kolekcji zwróconej przez `ConvertCollectionToUpperCase` , każdy element jest pobierany z tablicy ciągów źródłowych i konwertowany na wielkie przed pobraniem następnego elementu z tablicy ciągów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="30f53-110">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="30f53-111">Można zobaczyć, że cała tablica ciągów nie jest konwertowana na wielkie przed każdym elementem w zwróconej kolekcji w `foreach` pętli w `Main` .</span><span class="sxs-lookup"><span data-stu-id="30f53-111">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="30f53-112">W następnym temacie w tym samouczku przedstawiono Łączenie łańcuchowe zapytań:</span><span class="sxs-lookup"><span data-stu-id="30f53-112">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="30f53-113">Przykład łańcucha zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="30f53-113">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="30f53-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30f53-114">See also</span></span>

- [<span data-ttu-id="30f53-115">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="30f53-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
