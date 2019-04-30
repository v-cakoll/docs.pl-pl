---
title: Przykład wykonania odroczonego (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 9697f3e4c120c7d8bc184181ad99df08634e791e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702571"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="aacdc-102">Przykład wykonania odroczonego (C#)</span><span class="sxs-lookup"><span data-stu-id="aacdc-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="aacdc-103">W tym temacie przedstawiono sposób odroczonego wykonania i obliczanie z opóźnieniem wpływa na wykonywanie Twojego zapytaniach składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="aacdc-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aacdc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="aacdc-104">Example</span></span>  
 <span data-ttu-id="aacdc-105">Poniższy przykład pokazuje kolejność wykonywania, korzystając z metody rozszerzenia, która używa odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="aacdc-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="aacdc-106">Przykład deklaruje tablicę trzy ciągi.</span><span class="sxs-lookup"><span data-stu-id="aacdc-106">The example declares an array of three strings.</span></span> <span data-ttu-id="aacdc-107">Następnie wykonuje iterację przez zbiorze zwróconym przez `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="aacdc-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="aacdc-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="aacdc-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="aacdc-109">Należy zauważyć, że podczas iteracji w kolekcji zwróconej przez `ConvertCollectionToUpperCase`, każdy element jest pobierana z tablicy ciągów źródłowych i przekonwertowane na wielkie litery przed następnego elementu jest pobierana z tablicy ciągów źródła.</span><span class="sxs-lookup"><span data-stu-id="aacdc-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="aacdc-110">Widać, że całej tablicy ciągów nie jest konwertowana na wielkie litery, przetworzenia każdego elementu w kolekcji zwrócone `foreach` pętli w `Main`.</span><span class="sxs-lookup"><span data-stu-id="aacdc-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="aacdc-111">Następny temat w tym samouczku przedstawiono łańcucha zapytań razem:</span><span class="sxs-lookup"><span data-stu-id="aacdc-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="aacdc-112">Przykład łączenia łańcuchowego zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="aacdc-112">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="aacdc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aacdc-113">See also</span></span>

- [<span data-ttu-id="aacdc-114">Samouczek: Łączenie łańcuchowe zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="aacdc-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
