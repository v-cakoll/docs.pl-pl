---
title: Przykład odroczonego wykonania (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204135"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="fbd83-102">Przykład odroczonego wykonania (C#)</span><span class="sxs-lookup"><span data-stu-id="fbd83-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="fbd83-103">W tym temacie pokazano, jak odroczone wykonanie i leniwa ocena wpływa na wykonywanie linq do zapytań XML.</span><span class="sxs-lookup"><span data-stu-id="fbd83-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbd83-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbd83-104">Example</span></span>  
 <span data-ttu-id="fbd83-105">W poniższym przykładzie przedstawiono kolejność wykonywania przy użyciu metody rozszerzenia, która używa odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="fbd83-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="fbd83-106">W przykładzie deklaruje tablicy trzech ciągów.</span><span class="sxs-lookup"><span data-stu-id="fbd83-106">The example declares an array of three strings.</span></span> <span data-ttu-id="fbd83-107">Następnie iteruje przez kolekcję `ConvertCollectionToUpperCase`zwróconą przez .</span><span class="sxs-lookup"><span data-stu-id="fbd83-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="fbd83-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fbd83-108">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="fbd83-109">Należy zauważyć, że podczas iteracji `ConvertCollectionToUpperCase`za pośrednictwem kolekcji zwracanej przez , każdy element jest pobierany z tablicy ciągu źródłowego i konwertowane na wielkie litery przed następnym elementem jest pobierana z tablicy ciągów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="fbd83-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="fbd83-110">Widać, że cała tablica ciągów nie jest konwertowana na wielkie litery, zanim `foreach` każdy `Main`element w zwróconej kolekcji jest przetwarzany w pętli w .</span><span class="sxs-lookup"><span data-stu-id="fbd83-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="fbd83-111">Następny temat w tym samouczku ilustruje łączenie zapytań razem:</span><span class="sxs-lookup"><span data-stu-id="fbd83-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="fbd83-112">Przykład kwerend łańcuchowych (C#)</span><span class="sxs-lookup"><span data-stu-id="fbd83-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbd83-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbd83-113">See also</span></span>

- [<span data-ttu-id="fbd83-114">Samouczek: Łączenie zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="fbd83-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
