---
title: Przechowywanie wyników zapytania w pamięci
description: Sposób przechowywania wyników.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633567"
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="d04f7-103">Przechowywanie wyników zapytania w pamięci</span><span class="sxs-lookup"><span data-stu-id="d04f7-103">Store the results of a query in memory</span></span>

<span data-ttu-id="d04f7-104">Zapytanie jest po prostu zestaw instrukcji dotyczących sposobu pobierania i organizowania danych.</span><span class="sxs-lookup"><span data-stu-id="d04f7-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="d04f7-105">Zapytania są wykonywane opóźnieniem, zgodnie z żądaniem jest każdy element kolejne w wyniku.</span><span class="sxs-lookup"><span data-stu-id="d04f7-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="d04f7-106">Kiedy używasz `foreach` do iteracji wyników, elementy są zwracane jako dostępne.</span><span class="sxs-lookup"><span data-stu-id="d04f7-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="d04f7-107">Ocena zapytania i przechowywać wyniki bez wykonywania `foreach` pętli, po prostu wywołać jedną z następujących metod w zmiennej zapytania:</span><span class="sxs-lookup"><span data-stu-id="d04f7-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 <span data-ttu-id="d04f7-108">Zaleca się, czy podczas można przechowywać wyników zapytania, można przypisać obiektu zwróconego kolekcji do nowej zmiennej jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d04f7-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>

## <a name="example"></a><span data-ttu-id="d04f7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d04f7-109">Example</span></span>

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a><span data-ttu-id="d04f7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d04f7-110">See also</span></span>

- [<span data-ttu-id="d04f7-111">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d04f7-111">Language Integrated Query (LINQ)</span></span>](index.md)
