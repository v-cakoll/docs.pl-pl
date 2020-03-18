---
title: 'Porady: używanie ForEach do usuwanie elementów BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711236"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="d8fa0-102">Porady: używanie ForEach do usuwanie elementów BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="d8fa0-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>

<span data-ttu-id="d8fa0-103">Oprócz pobierania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> za <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> pomocą <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody i, można również użyć [foreach](../../../csharp/language-reference/keywords/foreach-in.md) [(For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w języku Visual Basic), aby usunąć elementy, dopóki dodawanie nie zostanie zakończona, a kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="d8fa0-104">Jest to nazywane *mutowanie wyliczenia* lub *zużywa wyliczenie,* ponieważ w przeciwieństwie do typowej `foreach` (`For Each`) pętli, ten wyliczacz modyfikuje kolekcji źródłowej przez usunięcie elementów.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="d8fa0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8fa0-105">Example</span></span>

<span data-ttu-id="d8fa0-106">W poniższym przykładzie pokazano, jak <xref:System.Collections.Concurrent.BlockingCollection%601> usunąć `foreach` wszystkie`For Each`elementy w pętli () za pomocą ( ).</span><span class="sxs-lookup"><span data-stu-id="d8fa0-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="d8fa0-107">W tym `foreach` przykładzie używa <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> pętli z metodą w wątku zużywa, co powoduje, że każdy element, który ma zostać usunięty z kolekcji, jak jest wyliczany.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="d8fa0-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="d8fa0-109">Wyliczanie kolekcji w ten sposób blokuje wątek konsumenta, jeśli nie są dostępne żadne elementy lub jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="d8fa0-110">W tym przykładzie blokowanie nie jest problemem, ponieważ wątek producenta dodaje elementy szybciej niż mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="d8fa0-111">Nie ma żadnej gwarancji, że elementy są wyliczane w tej samej kolejności, w jakiej są dodawane przez wątki producenta.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>

<span data-ttu-id="d8fa0-112">Aby wyliczyć kolekcję bez modyfikowania `foreach` `For Each`jej, <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> po prostu użyj ( ) bez metody.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="d8fa0-113">Jednak ważne jest, aby zrozumieć, że tego rodzaju wyliczenia reprezentuje migawkę kolekcji w określonym momencie w czasie.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="d8fa0-114">Jeśli inne wątki są dodawanie lub usuwanie elementów jednocześnie podczas wykonywania pętli, a następnie pętli może nie reprezentować rzeczywisty stan kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d8fa0-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8fa0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8fa0-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="d8fa0-116">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="d8fa0-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
