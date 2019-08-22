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
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666540"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="e5ea5-102">Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="e5ea5-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="e5ea5-103">Oprócz przejmowania <xref:System.Collections.Concurrent.BlockingCollection%601> elementów z przy <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> użyciu metody i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> można również użyć instrukcji [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w Visual Basic) do usuwania elementów do momentu ukończenia dodawania, a kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="e5ea5-104">Jest to nazywane *mutacją wyliczenia* lub zużywaniem, ponieważ, w przeciwieństwie do typowej`For Each` `foreach` pętli (), ten moduł wyliczający modyfikuje kolekcję źródłową, usuwając elementy.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="e5ea5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5ea5-105">Example</span></span>

<span data-ttu-id="e5ea5-106">Poniższy przykład pokazuje, jak usunąć wszystkie elementy w a <xref:System.Collections.Concurrent.BlockingCollection%601> za `foreach` pomocą pętli (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="e5ea5-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="e5ea5-107">W tym przykładzie zastosowano `foreach` pętlę <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> z metodą w wątku zużywania, która powoduje, że każdy element zostanie usunięty z kolekcji w miarę ich wyliczania.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="e5ea5-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="e5ea5-109">Wyliczenie kolekcji w ten sposób blokuje wątek odbiorcy, jeśli żadne elementy nie są dostępne lub jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="e5ea5-110">W tym przykładzie blokowanie nie jest problemem, ponieważ wątek produkcyjny dodaje elementy szybciej niż można ich użyć.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="e5ea5-111">Nie ma gwarancji, że elementy są wyliczane w tej samej kolejności, w jakiej są dodawane przez wątki producentów.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="e5ea5-112">Aby wyliczyć kolekcję bez modyfikacji, użyj `foreach` tylko (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="e5ea5-113">Jednak ważne jest, aby zrozumieć, że ten rodzaj wyliczenia reprezentuje migawkę kolekcji w określonym momencie.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="e5ea5-114">Jeśli inne wątki dodają lub usuwają elementy współbieżnie podczas wykonywania pętli, pętla może nie reprezentować rzeczywistego stanu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e5ea5-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5ea5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5ea5-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="e5ea5-116">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="e5ea5-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
