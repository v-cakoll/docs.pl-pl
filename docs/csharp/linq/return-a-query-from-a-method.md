---
title: Zwracanie zapytania z metody
description: Jak zwrócić zapytanie.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972523"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="c7305-103">Jak zwrócić zapytanie z metody (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="c7305-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="c7305-104">W tym przykładzie pokazano, jak zwrócić kwerendę z `out` metody jako wartość zwracaną i jako parametr.</span><span class="sxs-lookup"><span data-stu-id="c7305-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="c7305-105">Obiekty kwerendy można składać, co oznacza, że można zwrócić kwerendę z metody.</span><span class="sxs-lookup"><span data-stu-id="c7305-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="c7305-106">Obiekty reprezentujące kwerendy nie przechowują wynikowej kolekcji, ale raczej kroki, aby uzyskać wyniki w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="c7305-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="c7305-107">Zaletą zwracania obiektów kwerendy z metod jest to, że mogą być dalej składa się lub modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c7305-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="c7305-108">W związku z `out` tym każda wartość zwracana lub parametr metody, która zwraca kwerendę musi mieć również tego typu.</span><span class="sxs-lookup"><span data-stu-id="c7305-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="c7305-109">Jeśli metoda materializuje kwerendy do <xref:System.Collections.Generic.List%601> konkretnego <xref:System.Array> lub typu, jest uważany za zwracanie wyników kwerendy zamiast samej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c7305-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="c7305-110">Zmienna kwerendy, która jest zwracana z metody nadal mogą być składane lub modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c7305-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7305-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7305-111">Example</span></span>  
 <span data-ttu-id="c7305-112">W poniższym przykładzie pierwsza metoda zwraca kwerendę jako wartość zwracaną, a `out` druga metoda zwraca kwerendę jako parametr.</span><span class="sxs-lookup"><span data-stu-id="c7305-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="c7305-113">Należy zauważyć, że w obu przypadkach jest to kwerenda, która jest zwracana, a nie wyniki kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c7305-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="c7305-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7305-114">See also</span></span>

- [<span data-ttu-id="c7305-115">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c7305-115">Language Integrated Query (LINQ)</span></span>](index.md)
