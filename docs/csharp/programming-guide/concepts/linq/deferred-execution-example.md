---
title: "Wykonanie odroczone przykład (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b902c58f801a6e157a971335895670e8a8bf2181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="aeb08-102">Wykonanie odroczone przykład (C#)</span><span class="sxs-lookup"><span data-stu-id="aeb08-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="aeb08-103">W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie leniwe wpływa na wykonanie programu LINQ do XML zapytania.</span><span class="sxs-lookup"><span data-stu-id="aeb08-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb08-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aeb08-104">Example</span></span>  
 <span data-ttu-id="aeb08-105">W poniższym przykładzie przedstawiono kolejność wykonywania, korzystając z metody rozszerzenia, który używa odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="aeb08-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="aeb08-106">Przykład deklaruje tablicę trzy ciągi.</span><span class="sxs-lookup"><span data-stu-id="aeb08-106">The example declares an array of three strings.</span></span> <span data-ttu-id="aeb08-107">Go następnie iteruje po kolekcji zwróconej przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="aeb08-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="aeb08-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="aeb08-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="aeb08-109">Zwróć uwagę, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`każdego elementu jest pobierana z tablicy ciągów źródła i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.</span><span class="sxs-lookup"><span data-stu-id="aeb08-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="aeb08-110">Widać, że cała tablica ciągów nie jest przekonwertowany na wielkie litery, przed przetworzeniem każdego elementu w zwracanej kolekcji w `foreach` pętli w `Main`.</span><span class="sxs-lookup"><span data-stu-id="aeb08-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="aeb08-111">Następnego tematu w tym samouczku przedstawiono razem CBC zapytania:</span><span class="sxs-lookup"><span data-stu-id="aeb08-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
-   [<span data-ttu-id="aeb08-112">Tworzenie łańcuchów przykład kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="aeb08-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="aeb08-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aeb08-113">See Also</span></span>  
 [<span data-ttu-id="aeb08-114">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="aeb08-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
