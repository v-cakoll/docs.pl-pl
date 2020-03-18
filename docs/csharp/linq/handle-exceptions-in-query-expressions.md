---
title: Obsługa wyjątków w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wyjątki w wyrażeniach kwerend LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688504"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="87b50-103">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="87b50-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="87b50-104">Istnieje możliwość wywołania dowolnej metody w kontekście wyrażenia kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="87b50-105">Jednak zaleca się, aby uniknąć wywoływania dowolnej metody w wyrażeniu kwerendy, które można utworzyć efekt uboczny, takich jak modyfikowanie zawartości źródła danych lub zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="87b50-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="87b50-106">W tym przykładzie pokazano, jak uniknąć wywoływania wyjątków podczas wywoływania metod w wyrażeniu zapytania bez naruszania ogólnych wytycznych .NET dotyczących obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="87b50-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="87b50-107">Te wytyczne stwierdzają, że dopuszczalne jest, aby przechwycić określony wyjątek, gdy rozumiesz, dlaczego jest generowany w danym kontekście.</span><span class="sxs-lookup"><span data-stu-id="87b50-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="87b50-108">Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="87b50-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="87b50-109">W ostatnim przykładzie pokazano, jak obsługiwać te przypadki, gdy należy zgłosić wyjątek podczas wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="87b50-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="87b50-110">Example</span></span>

<span data-ttu-id="87b50-111">W poniższym przykładzie pokazano, jak przenieść kod obsługi wyjątków poza wyrażenie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="87b50-112">Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="87b50-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="87b50-113">Example</span></span>

<span data-ttu-id="87b50-114">W niektórych przypadkach najlepszą odpowiedzią na wyjątek, który jest generowany z poziomu kwerendy może być natychmiastowe zatrzymanie wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="87b50-115">W poniższym przykładzie pokazano, jak obsługiwać wyjątki, które mogą być generowane z wewnątrz treści kwerendy.</span><span class="sxs-lookup"><span data-stu-id="87b50-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="87b50-116">Załóżmy, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonania kwerendy, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="87b50-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="87b50-117">Należy zauważyć, że `try` blok `foreach` otacza pętlę, a nie samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="87b50-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="87b50-118">Jest to `foreach` spowodowane pętli jest punkt, w którym kwerenda jest faktycznie wykonywana.</span><span class="sxs-lookup"><span data-stu-id="87b50-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="87b50-119">Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="87b50-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="87b50-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87b50-120">See also</span></span>

- [<span data-ttu-id="87b50-121">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="87b50-121">Language Integrated Query (LINQ)</span></span>](index.md)
