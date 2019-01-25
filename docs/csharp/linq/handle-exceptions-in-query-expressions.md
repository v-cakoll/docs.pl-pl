---
title: Obsługa wyjątków w wyrażeniach zapytań (LINQ w C#)
description: Informacje o sposobie obsługi wyjątków w wyrażeniach zapytań LINQ w C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857505"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="8bbe8-103">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="8bbe8-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="8bbe8-104">Istnieje możliwość wywołać dowolną metodę w kontekście wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="8bbe8-105">Jednak zaleca się unikać wywołaniem jakiejkolwiek jego metody w wyrażeniu zapytania, które można utworzyć efekt uboczny, takich jak modyfikowanie zawartości źródła danych lub zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="8bbe8-106">W tym przykładzie pokazano, jak można uniknąć zgłaszania wyjątków, po wywołaniu metody w wyrażeniu zapytania bez naruszania ogólne wytyczne .NET na obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="8bbe8-107">Stan tych wytycznych można przechwytywać określony wyjątek, jeśli zrozumiesz, dlaczego jest zgłaszany w danym kontekście.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="8bbe8-108">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="8bbe8-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="8bbe8-109">W ostatnim przykładzie pokazano sposób obsługi tych przypadków, gdy należy zgłosić wyjątek podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="8bbe8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bbe8-110">Example</span></span>

<span data-ttu-id="8bbe8-111">Poniższy przykład przedstawia sposób przenoszenia kodu poza wyrażeniem zapytania obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="8bbe8-112">Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="8bbe8-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bbe8-113">Example</span></span>

<span data-ttu-id="8bbe8-114">W niektórych przypadkach może być najlepsze odpowiedzi na wyjątek, który jest zgłaszany w obrębie zapytania natychmiast zatrzymać wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="8bbe8-115">Poniższy przykład przedstawia sposób obsługi wyjątków, które może być wyrzucanych z wewnątrz treść zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="8bbe8-116">Przyjęto założenie, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonywania zapytania, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="8bbe8-117">Należy pamiętać, że `try` otacza bloku `foreach` pętli i nie zapytanie.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="8bbe8-118">Jest to spowodowane `foreach` pętli to punkt, w którym faktycznie wykonać zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bbe8-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="8bbe8-119">Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="8bbe8-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="8bbe8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bbe8-120">See also</span></span>

- [<span data-ttu-id="8bbe8-121">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8bbe8-121">Language Integrated Query (LINQ)</span></span>](index.md)
