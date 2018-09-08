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
ms.openlocfilehash: 2e2e312668a7cf4fe39596ae018adaf62cd850e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187549"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Porady: użycie tablic kolekcji blokujących w potoku
Poniższy przykład pokazuje, jak używać tablic <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiektów za pomocą metod statycznych, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> do zaimplementowania szybkie i elastyczne transfer danych między składnikami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano implementację podstawowy potok, w którym każdy obiekt jest przy równoczesnym danych z kolekcji danych wejściowych, przekształcania i przekazywania go do kolekcji danych wyjściowych.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
