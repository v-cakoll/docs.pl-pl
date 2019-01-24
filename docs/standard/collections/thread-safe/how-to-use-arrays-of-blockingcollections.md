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
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627203"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Instrukcje: Używanie tablic kolekcji blokujących w potoku
Poniższy przykład pokazuje, jak używać tablic <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiektów za pomocą metod statycznych, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> do zaimplementowania szybkie i elastyczne transfer danych między składnikami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano implementację podstawowy potok, w którym każdy obiekt jest przy równoczesnym danych z kolekcji danych wejściowych, przekształcania i przekazywania go do kolekcji danych wyjściowych.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
