---
title: Zwracanie kwerendy z metody
description: "Sposób zwracania zapytania."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="194b3-104">Porady: zwracanie zapytania z metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="194b3-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="194b3-105">W tym przykładzie pokazano, jak zwracanie kwerendy z metody jako wartość zwracaną, a `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="194b3-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="194b3-106">Obiekty zapytania są zezwala na składanie, co oznacza, że można zwracanie kwerendy z metody.</span><span class="sxs-lookup"><span data-stu-id="194b3-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="194b3-107">Obiekty, które reprezentują zapytania nie należy przechowywać wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="194b3-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="194b3-108">Zaletą zwracać obiekty zapytania z metody jest że mogą zostać dalsze składane albo zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="194b3-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="194b3-109">W związku z tym wszelkie zwracać wartość lub `out` parametru metody, która zwraca zapytania musi mieć również tego typu.</span><span class="sxs-lookup"><span data-stu-id="194b3-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="194b3-110">Jeśli metoda zostaje kwerendy do konkretnych <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki zapytania, zamiast samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="194b3-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="194b3-111">Można nadal składa się zmienną zapytania, która jest zwracana z metody lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="194b3-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="194b3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="194b3-112">Example</span></span>  
 <span data-ttu-id="194b3-113">W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracane, a druga metoda zwraca zapytanie jako `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="194b3-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="194b3-114">Należy pamiętać, że w obu przypadkach kwerendę, która jest zwracana nie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="194b3-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="194b3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="194b3-115">See Also</span></span>  
 [<span data-ttu-id="194b3-116">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="194b3-116">LINQ Query Expressions</span></span>](index.md)
