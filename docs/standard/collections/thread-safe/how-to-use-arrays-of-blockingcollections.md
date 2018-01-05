---
title: "Porady: użycie tablic kolekcji blokujących w potoku"
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
helpviewer_keywords: thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 753c58686e943f5753c76a8d695f4401c4a69952
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Porady: użycie tablic kolekcji blokujących w potoku
Poniższy przykład przedstawia użycie tablic <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiekty z metody statyczne, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> do zaimplementowania danych szybkie i elastyczne transferu między składnikami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano implementację podstawowego potoku, w którym każdy obiekt jest przy równoczesnym danych wejściowych kolekcji, przekształcania i przekazaniem ich do kolekcji danych wyjściowych.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
