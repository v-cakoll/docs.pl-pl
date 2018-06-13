---
title: 'Porady: użycie tablic kolekcji blokujących w potoku'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9313f1064534702fdc2d239eb7f0f69a470329e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567773"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="e9dd4-102">Porady: użycie tablic kolekcji blokujących w potoku</span><span class="sxs-lookup"><span data-stu-id="e9dd4-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="e9dd4-103">Poniższy przykład przedstawia użycie tablic <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiekty z metody statyczne, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> do zaimplementowania danych szybkie i elastyczne transferu między składnikami.</span><span class="sxs-lookup"><span data-stu-id="e9dd4-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9dd4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9dd4-104">Example</span></span>  
 <span data-ttu-id="e9dd4-105">W poniższym przykładzie pokazano implementację podstawowego potoku, w którym każdy obiekt jest przy równoczesnym danych wejściowych kolekcji, przekształcania i przekazaniem ich do kolekcji danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e9dd4-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="e9dd4-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9dd4-106">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="e9dd4-107">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="e9dd4-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
