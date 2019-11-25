---
title: Zwracanie zapytania z metody
description: Jak zwrócić zapytanie.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972523"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="ca0cb-103">Jak zwrócić zapytanie z metody (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="ca0cb-103">How to return a query from a method (C# Programming Guide)</span></span>
<span data-ttu-id="ca0cb-104">Ten przykład przedstawia sposób zwrócenia zapytania z metody jako wartości zwracanej i jako parametru `out`.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="ca0cb-105">Obiekty zapytań są możliwe do redagowania, co oznacza, że można zwrócić zapytanie z metody.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="ca0cb-106">Obiekty reprezentujące zapytania nie przechowują wynikowej kolekcji, ale zamiast kroków w celu wygenerowania wyników w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="ca0cb-107">Zaletą zwracania obiektów zapytań z metod jest, że mogą one być bardziej złożone lub zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="ca0cb-108">W związku z tym każda wartość zwracana lub `out` parametr metody, która zwraca zapytanie, musi również mieć ten typ.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="ca0cb-109">Jeśli metoda materializuje zapytanie w konkretną <xref:System.Collections.Generic.List%601> lub <xref:System.Array>, jest uznawane za zwracające wyniki zapytania zamiast samego zapytania.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="ca0cb-110">Zmienna zapytania, która jest zwracana z metody, może być w dalszym ciągu złożona lub zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca0cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca0cb-111">Example</span></span>  
 <span data-ttu-id="ca0cb-112">W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartość zwracaną, a druga metoda zwraca zapytanie jako parametr `out`.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="ca0cb-113">Należy zauważyć, że w obu przypadkach jest to zapytanie, które jest zwracane, a nie wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="ca0cb-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="ca0cb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca0cb-114">See also</span></span>

- [<span data-ttu-id="ca0cb-115">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ca0cb-115">Language Integrated Query (LINQ)</span></span>](index.md)
