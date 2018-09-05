---
title: Store wyniki zapytania w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 98a300b2c11eb037ed4ce34caea2673a4e0f8e6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525233"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="e827e-103">Store wyniki zapytania w pamięci</span><span class="sxs-lookup"><span data-stu-id="e827e-103">Store the results of a query in memory</span></span>

<span data-ttu-id="e827e-104">Zapytanie jest po prostu zestaw instrukcji dotyczących sposobu pobierania i organizowania danych.</span><span class="sxs-lookup"><span data-stu-id="e827e-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="e827e-105">Zapytania są wykonywane opóźnieniem, zgodnie z żądaniem jest każdy element kolejne w wyniku.</span><span class="sxs-lookup"><span data-stu-id="e827e-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="e827e-106">Kiedy używasz `foreach` do iteracji wyników, elementy są zwracane jako dostępne.</span><span class="sxs-lookup"><span data-stu-id="e827e-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="e827e-107">Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołać jedną z następujących metod w zmiennej zapytania:</span><span class="sxs-lookup"><span data-stu-id="e827e-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="e827e-108">Zaleca się, czy podczas można przechowywać wyników zapytania, można przypisać obiektu zwróconego kolekcji do nowej zmiennej jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e827e-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="e827e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e827e-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="e827e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e827e-110">See also</span></span>

- [<span data-ttu-id="e827e-111">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e827e-111">Language Integrated Query (LINQ)</span></span>](index.md)