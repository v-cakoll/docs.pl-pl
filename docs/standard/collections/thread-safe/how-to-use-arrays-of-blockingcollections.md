---
title: 'Instrukcje: Używanie tablic kolekcji blokujących w potoku'
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
ms.openlocfilehash: a4667d78fdf91a3e62c22d88c7cbe9effaae57d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923373"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="7288c-102">Instrukcje: Używanie tablic kolekcji blokujących w potoku</span><span class="sxs-lookup"><span data-stu-id="7288c-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="7288c-103">Poniższy przykład pokazuje, jak używać tablic <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiektów za pomocą metod statycznych, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> do zaimplementowania szybkie i elastyczne transfer danych między składnikami.</span><span class="sxs-lookup"><span data-stu-id="7288c-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7288c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7288c-104">Example</span></span>  
 <span data-ttu-id="7288c-105">W poniższym przykładzie pokazano implementację podstawowy potok, w którym każdy obiekt jest przy równoczesnym danych z kolekcji danych wejściowych, przekształcania i przekazywania go do kolekcji danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7288c-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="7288c-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7288c-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="7288c-107">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="7288c-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
