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
ms.openlocfilehash: 397c438bacd1cfed1613efef61e9d7266d55ea47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711262"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Porady: użycie tablic kolekcji blokujących w potoku
W poniższym przykładzie pokazano, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> jak używać tablic <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> obiektów <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> z metodami statycznymi, takimi jak i implementować szybki i elastyczny transfer danych między składnikami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono implementacji podstawowego potoku, w którym każdy obiekt jest jednocześnie biorąc dane z kolekcji danych wejściowych, przekształcając go i przekazując go do kolekcji danych wyjściowych.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
