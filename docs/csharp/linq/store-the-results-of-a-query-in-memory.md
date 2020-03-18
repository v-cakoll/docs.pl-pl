---
title: Przechowywanie wyników zapytania w pamięci
description: Jak przechowywać wyniki.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633567"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="23faf-103">Przechowywanie wyników zapytania w pamięci</span><span class="sxs-lookup"><span data-stu-id="23faf-103">Store the results of a query in memory</span></span>

<span data-ttu-id="23faf-104">Kwerenda jest w zasadzie zestaw instrukcji dotyczących pobierania i organizowania danych.</span><span class="sxs-lookup"><span data-stu-id="23faf-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="23faf-105">Zapytania są wykonywane leniwie, jak każdy kolejny element w wyniku jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="23faf-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="23faf-106">Gdy używasz `foreach` do iterate wyników, elementy są zwracane jako dostęp.</span><span class="sxs-lookup"><span data-stu-id="23faf-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="23faf-107">Aby ocenić kwerendę i przechowywać `foreach` jej wyniki bez wykonywania pętli, wystarczy wywołać jedną z następujących metod na zmiennej kwerendy:</span><span class="sxs-lookup"><span data-stu-id="23faf-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="23faf-108">Zaleca się, aby podczas przechowywania wyników kwerendy przypisano zwrócony obiekt kolekcji do nowej zmiennej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="23faf-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="23faf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="23faf-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="23faf-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23faf-110">See also</span></span>

- [<span data-ttu-id="23faf-111">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="23faf-111">Language Integrated Query (LINQ)</span></span>](index.md)
