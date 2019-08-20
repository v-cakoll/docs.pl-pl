---
title: Przykład wykonania odroczonego (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: a934645d0d7ad807e1524031ca3f023f7b11c5b4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594546"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="17076-102">Przykład wykonania odroczonego (C#)</span><span class="sxs-lookup"><span data-stu-id="17076-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="17076-103">W tym temacie pokazano, w jaki sposób odroczone wykonywanie i Ocena z opóźnieniem wpływają na wykonywanie zapytań LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="17076-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17076-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="17076-104">Example</span></span>  
 <span data-ttu-id="17076-105">Poniższy przykład pokazuje kolejność wykonywania przy użyciu metody rozszerzenia, która korzysta z odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="17076-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="17076-106">Przykład deklaruje tablicę trzech ciągów.</span><span class="sxs-lookup"><span data-stu-id="17076-106">The example declares an array of three strings.</span></span> <span data-ttu-id="17076-107">Następnie wykonuje iterację w kolekcji zwróconej przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="17076-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="17076-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="17076-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="17076-109">Należy zauważyć, że podczas iteracji kolekcji zwróconej `ConvertCollectionToUpperCase`przez, każdy element jest pobierany z tablicy ciągów źródłowych i konwertowany na wielkie przed pobraniem następnego elementu z tablicy ciągów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="17076-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="17076-110">Można zobaczyć, że cała tablica ciągów nie jest konwertowana na wielkie przed każdym elementem w zwróconej kolekcji w `foreach` pętli w. `Main`</span><span class="sxs-lookup"><span data-stu-id="17076-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="17076-111">W następnym temacie w tym samouczku przedstawiono Łączenie łańcuchowe zapytań:</span><span class="sxs-lookup"><span data-stu-id="17076-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="17076-112">Przykład łańcucha kwerend (C#)</span><span class="sxs-lookup"><span data-stu-id="17076-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="17076-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17076-113">See also</span></span>

- [<span data-ttu-id="17076-114">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="17076-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
