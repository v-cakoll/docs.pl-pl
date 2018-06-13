---
title: Zwracanie kwerendy z metody
description: Sposób zwracania zapytania.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274953"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="51705-103">Porady: zwracanie zapytania z metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="51705-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="51705-104">W tym przykładzie pokazano, jak zwracanie kwerendy z metody jako wartość zwracaną, a `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="51705-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="51705-105">Obiekty zapytania są zezwala na składanie, co oznacza, że można zwracanie kwerendy z metody.</span><span class="sxs-lookup"><span data-stu-id="51705-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="51705-106">Obiekty, które reprezentują zapytania nie należy przechowywać wynikowy kolekcji, ale raczej kroki w celu uzyskania wyników w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="51705-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="51705-107">Zaletą zwracać obiekty zapytania z metody jest że mogą zostać dalsze składane albo zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="51705-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="51705-108">W związku z tym wszelkie zwracać wartość lub `out` parametru metody, która zwraca zapytania musi mieć również tego typu.</span><span class="sxs-lookup"><span data-stu-id="51705-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="51705-109">Jeśli metoda zostaje kwerendy do konkretnych <xref:System.Collections.Generic.List%601> lub <xref:System.Array> typu, jest on uznawany za zwracać wyniki zapytania, zamiast samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="51705-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="51705-110">Można nadal składa się zmienną zapytania, która jest zwracana z metody lub zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="51705-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51705-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="51705-111">Example</span></span>  
 <span data-ttu-id="51705-112">W poniższym przykładzie pierwsza metoda zwraca zapytanie jako wartości zwracane, a druga metoda zwraca zapytanie jako `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="51705-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="51705-113">Należy pamiętać, że w obu przypadkach kwerendę, która jest zwracana nie wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="51705-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="51705-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51705-114">See Also</span></span>  
 [<span data-ttu-id="51705-115">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="51705-115">LINQ Query Expressions</span></span>](index.md)
