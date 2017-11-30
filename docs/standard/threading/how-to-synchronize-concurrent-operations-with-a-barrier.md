---
title: "Porady: synchronizacja jednoczesnych operacji za pomocą bariery"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Porady: synchronizacja jednoczesnych operacji za pomocą bariery
Poniższy przykład przedstawia sposób synchronizowanie równoczesnych zadań z <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Przykład  
 Następujący program ma zliczania liczby iteracji (lub faz) są wymagane dwa wątków do każdego Znajdź ich połowie rozwiązania do tej samej fazy za pomocą algorytmu randomizing zamieniać wyrazy. Po każdy wątek jest przemieszane jego wyrazy, operacji po fazie bariery porównuje dwa wyników, aby zobaczyć, czy pełnym zdaniem zostało wyrenderowane w odpowiedniej kolejności programu word.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> jest obiekt, który uniemożliwia pojedynczych zadań w operacji równoległej przed kontynuowaniem, aż zostanie bariera wszystkie zadania. Jest przydatne w przypadku operacji równoległej odbywa się w fazach i każdej fazy wymaga synchronizacji między zadaniami. W tym przykładzie są dwie fazy, aby wykonać operację. W pierwszej fazie każdego zadania wypełnia sekcji buforu z danymi. Po zakończeniu każdego zadania wypełnianie sekcji zadanie sygnalizuje bariery, który jest gotowy kontynuować, a następnie czeka. Gdy wszystkie zadania mają sygnalizowane bariery, są one odblokowane i uruchamia na drugim etapie. Bariera jest konieczne, ponieważ na drugim etapie musi mieć wszystkie zadania dostępu do wszystkich danych, który został wygenerowany w tym punkcie. Bez bariery pierwszego zadania do wykonania może podjąć próbę odczytu z buforów, które nie zostały wypełnione jeszcze przez inne zadania. Możesz zsynchronizować dowolną liczbę etapów w ten sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
