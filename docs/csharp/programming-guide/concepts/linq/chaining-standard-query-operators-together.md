---
title: "CBC standardowych operatorów zapytań razem (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 47e936bffd79784b0ee6850bfc29d1d1f5b3224d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="8aeec-102">CBC standardowych operatorów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="8aeec-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="8aeec-103">Jest ostatnim tematu w [samouczek: tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) samouczka.</span><span class="sxs-lookup"><span data-stu-id="8aeec-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) tutorial.</span></span>  
  
 <span data-ttu-id="8aeec-104">Standardowe operatory zapytań można również zostaną połączone.</span><span class="sxs-lookup"><span data-stu-id="8aeec-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="8aeec-105">Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatora, a także działa w sposób opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="8aeec-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="8aeec-106">Brak wyników pośrednich materializować są przez nią.</span><span class="sxs-lookup"><span data-stu-id="8aeec-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aeec-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8aeec-107">Example</span></span>  
 <span data-ttu-id="8aeec-108">W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="8aeec-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="8aeec-109"><xref:System.Linq.Enumerable.Where%2A> Metoda działa w prawie dokładnie tak samo jak opóźnieniem metody używane w poprzednich przykładach, w tym samouczku `ConvertCollectionToUpperCase` i `AppendString`.</span><span class="sxs-lookup"><span data-stu-id="8aeec-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="8aeec-110">Jedną różnicą jest to, że w takim przypadku <xref:System.Linq.Enumerable.Where%2A> metody iteruje po jego kolekcji źródłowej Określa pierwszy element predykatu nie zostały spełnione, a następnie pobiera następnego elementu przekazywania.</span><span class="sxs-lookup"><span data-stu-id="8aeec-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="8aeec-111">Powoduje ona następnie drugiego elementu.</span><span class="sxs-lookup"><span data-stu-id="8aeec-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="8aeec-112">Jednak podstawową koncepcją jest taka sama: pośredni kolekcje nie są zmaterializowany, chyba że mają być.</span><span class="sxs-lookup"><span data-stu-id="8aeec-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="8aeec-113">W przypadku używania wyrażenia zapytania są konwertowane na wywołania standardowych operatorów zapytań i Zastosuj te same zasady.</span><span class="sxs-lookup"><span data-stu-id="8aeec-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="8aeec-114">Przykłady w tej sekcji, w których jest kwerenda dokumentów pakietu Office Open XML używają tej samej zasadzie.</span><span class="sxs-lookup"><span data-stu-id="8aeec-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="8aeec-115">Wykonanie odroczone i obliczanie leniwe przedstawiono niektóre podstawowe założenia, że rozumiesz musi wykorzystywać LINQ (i LINQ do XML).</span><span class="sxs-lookup"><span data-stu-id="8aeec-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
            where s.CompareTo("D") >= 0  
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
  
 <span data-ttu-id="8aeec-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8aeec-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a><span data-ttu-id="8aeec-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8aeec-117">See Also</span></span>  
 [<span data-ttu-id="8aeec-118">Samouczek: Tworzenie łańcuchów zapytań razem (C#)</span><span class="sxs-lookup"><span data-stu-id="8aeec-118">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
