---
title: Przechowywanie wyników kwerendy w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279636"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="b8b78-103">Przechowywanie wyników kwerendy w pamięci</span><span class="sxs-lookup"><span data-stu-id="b8b78-103">Store the results of a query in memory</span></span>

<span data-ttu-id="b8b78-104">Zapytanie jest zasadniczo zestaw instrukcji dotyczących sposobu pobierania i organizowania danych.</span><span class="sxs-lookup"><span data-stu-id="b8b78-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="b8b78-105">Zapytania są wykonywane w trybie opóźnienia, żądaną każdego elementu kolejnych w wyniku.</span><span class="sxs-lookup"><span data-stu-id="b8b78-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="b8b78-106">Jeśli używasz `foreach` iteracyjne wyniki, elementy są zwracane jako dostępne.</span><span class="sxs-lookup"><span data-stu-id="b8b78-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="b8b78-107">Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołaj jedną z następujących metod na zmienną zapytania:</span><span class="sxs-lookup"><span data-stu-id="b8b78-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="b8b78-108">Zaleca się, czy podczas przechowywania wyników zapytania, można przypisać obiektu zwracana kolekcja do nowej zmiennej jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b8b78-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b78-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8b78-109">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="b8b78-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8b78-110">See Also</span></span>  
 [<span data-ttu-id="b8b78-111">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="b8b78-111">LINQ Query Expressions</span></span>](index.md)
