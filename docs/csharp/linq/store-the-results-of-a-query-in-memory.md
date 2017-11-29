---
title: "Przechowywanie wyników kwerendy w pamięci"
description: "Sposób przechowywania wyników."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="51d4b-104">Przechowywanie wyników kwerendy w pamięci</span><span class="sxs-lookup"><span data-stu-id="51d4b-104">Store the results of a query in memory</span></span>

<span data-ttu-id="51d4b-105">Zapytanie jest zasadniczo zestaw instrukcji dotyczących sposobu pobierania i organizowania danych.</span><span class="sxs-lookup"><span data-stu-id="51d4b-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="51d4b-106">Zapytania są wykonywane w trybie opóźnienia, żądaną każdego elementu kolejnych w wyniku.</span><span class="sxs-lookup"><span data-stu-id="51d4b-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="51d4b-107">Jeśli używasz `foreach` iteracyjne wyniki, elementy są zwracane jako dostępne.</span><span class="sxs-lookup"><span data-stu-id="51d4b-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="51d4b-108">Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołaj jedną z następujących metod na zmienną zapytania:</span><span class="sxs-lookup"><span data-stu-id="51d4b-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="51d4b-109">Zaleca się, czy podczas przechowywania wyników zapytania, można przypisać obiektu zwracana kolekcja do nowej zmiennej jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="51d4b-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="51d4b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="51d4b-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="51d4b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51d4b-111">See Also</span></span>  
 [<span data-ttu-id="51d4b-112">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="51d4b-112">LINQ Query Expressions</span></span>](index.md)
