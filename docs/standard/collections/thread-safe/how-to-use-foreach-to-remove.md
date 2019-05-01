---
title: 'Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d13f123953c32cae01df501c0e251ec29b0478b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937452"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="55a17-102">Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="55a17-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="55a17-103">Oprócz wykonywania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> przy użyciu <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, można również użyć [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([dla każdego](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) w języku Visual Basic) do usuwanie elementów, aż do dodawania ukończone i kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="55a17-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="55a17-104">Jest to nazywane *mutacja wyliczenie* lub *wykorzystywanie wyliczenie* , ponieważ w odróżnieniu od typowych `foreach` (`For Each`) pętli, ten moduł wyliczający modyfikuje kolekcji źródłowej, usuwając elementy.</span><span class="sxs-lookup"><span data-stu-id="55a17-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="55a17-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="55a17-105">Example</span></span>

<span data-ttu-id="55a17-106">Poniższy przykład pokazuje, jak usunąć wszystkie elementy w <xref:System.Collections.Concurrent.BlockingCollection%601> przy użyciu `foreach` (`For Each`) pętli.</span><span class="sxs-lookup"><span data-stu-id="55a17-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="55a17-107">W tym przykładzie użyto `foreach` pętli z <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metody w zużywającym wątku, co powoduje, że każdy element do usunięcia z kolekcji jest uprzednie.</span><span class="sxs-lookup"><span data-stu-id="55a17-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="55a17-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> Ogranicza maksymalną liczbę elementów znajdujących się w kolekcji, w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="55a17-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="55a17-109">Wyliczanie kolekcji w ten sposób blokuje wątku konsumenta, jeśli nie, nie są dostępne elementy, lub jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="55a17-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="55a17-110">W tym przykładzie blokowania nie ma znaczenia, ponieważ wątek producentów dodaje elementy szybciej niż mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="55a17-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="55a17-111">Nie ma żadnej gwarancji, że elementy są wyliczane w tej samej kolejności, dodawanych przez wątki producenta.</span><span class="sxs-lookup"><span data-stu-id="55a17-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="55a17-112">Wyliczyć kolekcji bez modyfikowania go, wystarczy użyć `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="55a17-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="55a17-113">Jednak ważne jest zrozumienie, że ten rodzaj wyliczenie reprezentuje migawkę kolekcji w określonym punkcie w czasie.</span><span class="sxs-lookup"><span data-stu-id="55a17-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="55a17-114">Jeśli inne wątki dodawania lub usuwania elementów równolegle, gdy są wykonywane pętli, pętla może reprezentuje rzeczywisty stan kolekcji.</span><span class="sxs-lookup"><span data-stu-id="55a17-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="55a17-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55a17-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="55a17-116">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="55a17-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
