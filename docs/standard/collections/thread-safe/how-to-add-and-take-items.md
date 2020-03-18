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
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711301"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="63f8e-102">Porady: dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="63f8e-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="63f8e-103">W tym przykładzie pokazano, jak <xref:System.Collections.Concurrent.BlockingCollection%601> dodawać i usuwać elementy z pliku w sposób blokujący i nieblokujący.</span><span class="sxs-lookup"><span data-stu-id="63f8e-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="63f8e-104">Aby uzyskać <xref:System.Collections.Concurrent.BlockingCollection%601>więcej informacji na temat , zobacz [BlockingCollection Omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63f8e-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="63f8e-105">Na przykład jak wyliczyć a <xref:System.Collections.Concurrent.BlockingCollection%601> dopóki nie jest pusty i nie więcej elementów zostaną dodane, zobacz [Jak: Użyj ForEach usunąć elementy w BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="63f8e-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="63f8e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f8e-106">Example</span></span>  
 <span data-ttu-id="63f8e-107">W tym pierwszym przykładzie pokazano, jak dodawać i przyjmować elementy, tak aby operacje blokowały, jeśli kolekcja jest tymczasowo pusta (podczas przyjmowania) lub przy maksymalnej pojemności (podczas dodawania) lub jeśli upłynął określony okres czasu.</span><span class="sxs-lookup"><span data-stu-id="63f8e-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="63f8e-108">Należy zauważyć, że blokowanie maksymalnej pojemności jest włączona tylko wtedy, gdy BlockingCollection został utworzony z maksymalną pojemnością określoną w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="63f8e-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="63f8e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f8e-109">Example</span></span>  
 <span data-ttu-id="63f8e-110">W tym drugim przykładzie pokazano, jak dodawać i przyjmować elementy, aby operacje nie blokowały.</span><span class="sxs-lookup"><span data-stu-id="63f8e-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="63f8e-111">Jeśli żaden element nie jest obecny, osiągnięto maksymalną pojemność ograniczonej kolekcji lub upłynął <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> okres czasu, a następnie lub operacja zwraca false.</span><span class="sxs-lookup"><span data-stu-id="63f8e-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="63f8e-112">Dzięki temu wątek do wykonywania innych przydatnych prac na chwilę, a następnie spróbuj ponownie później, aby pobrać nowy element lub spróbuj dodać ten sam element, który nie może być dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="63f8e-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="63f8e-113">Program pokazuje również, jak zaimplementować <xref:System.Collections.Concurrent.BlockingCollection%601>anulowanie podczas uzyskiwania dostępu do pliku .</span><span class="sxs-lookup"><span data-stu-id="63f8e-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="63f8e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63f8e-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="63f8e-115">BlockingCollection — Przegląd</span><span class="sxs-lookup"><span data-stu-id="63f8e-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
