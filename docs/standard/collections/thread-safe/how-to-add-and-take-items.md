---
title: "Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8abfe549c34310ce256632a3e3146ec925284361
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="60971-102">Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="60971-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="60971-103">W tym przykładzie pokazano, jak dodawać i usuwać elementy z <xref:System.Collections.Concurrent.BlockingCollection%601> w obu blokujące i nieblokujące sposób.</span><span class="sxs-lookup"><span data-stu-id="60971-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and non-blocking manner.</span></span> <span data-ttu-id="60971-104">Aby uzyskać więcej informacji na temat <xref:System.Collections.Concurrent.BlockingCollection%601>, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="60971-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="60971-105">Na przykład jak wyliczyć <xref:System.Collections.Concurrent.BlockingCollection%601> do czasu jest pusty i zostanie dodany ma więcej elementów, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)</span><span class="sxs-lookup"><span data-stu-id="60971-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="60971-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="60971-106">Example</span></span>  
 <span data-ttu-id="60971-107">Pierwszym przykładzie pokazano, jak na dodawanie i pobieranie elementów tak, aby operacje zablokują kolekcji jest tymczasowo pusta (podejmując) lub maksymalnej pojemności (podczas dodawania) lub określony limit czasu upłynął.</span><span class="sxs-lookup"><span data-stu-id="60971-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or a specified timeout period has elapsed.</span></span> <span data-ttu-id="60971-108">Należy pamiętać, że blokowania na maksymalną pojemność jest włączona tylko po utworzeniu kolekcji BlockingCollection o pojemności maksymalnej określonym w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="60971-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="60971-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="60971-109">Example</span></span>  
 <span data-ttu-id="60971-110">W tym drugim przykładzie przedstawiono sposób Dodawanie i pobieranie elementów, aby operacje nie powoduje blokowania.</span><span class="sxs-lookup"><span data-stu-id="60971-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="60971-111">Jeśli żaden element jest obecny, lub osiągnięto maksymalną pojemność kolekcji ograniczonego lub upłynął limit czasu, a następnie <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="60971-111">If no item is present, or maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="60971-112">Pozwala to na inne przydatne pracy dla chwilę i spróbuj ponownie później do pobrania nowego elementu, lub spróbuj dodać ten sam element, którego nie można dodać wcześniej wątku.</span><span class="sxs-lookup"><span data-stu-id="60971-112">This allows the thread to do some other useful work for awhile and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="60971-113">Program również pokazuje, jak wdrożyć anulowania podczas uzyskiwania dostępu do <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="60971-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="60971-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60971-114">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="60971-115">BlockingCollection — omówienie</span><span class="sxs-lookup"><span data-stu-id="60971-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
