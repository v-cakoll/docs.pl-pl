---
title: Zwracanie zapytania z metody
description: Jak zwracanie zapytania.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: fe2192a3edb683d7284ffae3b66cb9f70e8854b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519102"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="f6a1b-103">Instrukcje: Zwracanie zapytania z metody (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f6a1b-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="f6a1b-104">W tym przykładzie pokazano, jak zwracanie zapytania z metody jako wartość zwracaną i `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="f6a1b-105">Obiekty zapytania są konfigurowalna, co oznacza, że można zwracanie zapytania z metody.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="f6a1b-106">Nie należy przechowywać obiekty reprezentujące zapytań, wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników, w razie.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="f6a1b-107">Zaletą zwracać obiekty zapytania z metody jest, można je dodatkowo składa się lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="f6a1b-108">W związku z tym powrotnych wartość lub `out` parametru metody, która zwraca kwerendy musi również mieć tego typu.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="f6a1b-109">Jeśli metoda materializuje zapytania na konkretny <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki kwerendy zamiast samo zapytanie.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="f6a1b-110">Zmienna zapytania, który jest zwracany z metody można nadal składa się lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6a1b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6a1b-111">Example</span></span>  
 <span data-ttu-id="f6a1b-112">W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracanej, a druga metoda zwraca zapytanie jako `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="f6a1b-113">Należy pamiętać, że w obu przypadkach zapytanie, które ma zostać zwrócona, nie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="f6a1b-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="f6a1b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6a1b-114">See also</span></span>

- [<span data-ttu-id="f6a1b-115">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f6a1b-115">Language Integrated Query (LINQ)</span></span>](index.md)
