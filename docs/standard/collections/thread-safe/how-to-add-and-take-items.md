---
title: 'Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74518f6f56f65668d4c7f073a79c9e7de27d7978
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516662"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="6b44a-102">Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="6b44a-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="6b44a-103">W tym przykładzie przedstawiono sposób dodawania i usuwania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> blokowania i sposób bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="6b44a-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="6b44a-104">Aby uzyskać więcej informacji na temat <xref:System.Collections.Concurrent.BlockingCollection%601>, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6b44a-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="6b44a-105">Na przykład jak wyliczyć <xref:System.Collections.Concurrent.BlockingCollection%601> dopóki nie jest pusta i nie więcej elementy zostaną dodane, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="6b44a-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="6b44a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b44a-106">Example</span></span>  
 <span data-ttu-id="6b44a-107">W pierwszym przykładzie pokazano, jak dodawanie i elementy tak, aby operacje spowoduje zablokowanie, jeśli kolekcja jest albo tymczasowo puste (robiąc) lub na maksymalną pojemność (podczas dodawania) lub jeśli upłynął określony limit czasu.</span><span class="sxs-lookup"><span data-stu-id="6b44a-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="6b44a-108">Należy pamiętać, że blokowania na maksymalną pojemność jest włączony tylko BlockingCollection zostało utworzone z maksymalną pojemność określony w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="6b44a-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="6b44a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b44a-109">Example</span></span>  
 <span data-ttu-id="6b44a-110">Ten drugi przykład pokazuje, jak dodawanie i pobieranie elementów tak, aby operacje nie będzie blokować.</span><span class="sxs-lookup"><span data-stu-id="6b44a-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="6b44a-111">Jeśli element nie jest obecny, osiągnął maksymalną pojemność w kolekcji ograniczonego lub upłynął limit czasu, a następnie <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="6b44a-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="6b44a-112">Dzięki temu wątek wykonywania niektórych użytecznej pracy przez jakiś czas i spróbuj ponownie później do pobrania nowego elementu lub próba dodania tego samego elementu, którego nie można dodać wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6b44a-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="6b44a-113">Program ilustruje też sposób implementacji anulowania podczas uzyskiwania dostępu do <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="6b44a-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="6b44a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b44a-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [<span data-ttu-id="6b44a-115">BlockingCollection — omówienie</span><span class="sxs-lookup"><span data-stu-id="6b44a-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
