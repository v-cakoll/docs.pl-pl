---
title: 'Porady: synchronizacja jednoczesnych operacji za pomocą bariery'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44341923"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Porady: synchronizacja jednoczesnych operacji za pomocą bariery
Poniższy przykład pokazuje, jak synchronizować równoczesnych zadań za pomocą <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Przykład  
 Następujący program ma policzyć ile iteracji (lub fazy) są wymagane dla dwóch wątków do każdego znalezienia ich połowie rozwiązania do tej samej fazy za pomocą algorytmu randomizing zamieniać wyrazy. Po każdy wątek ma przekazanych jego słów, operację po fazie bariery porównuje dwa wyniki, aby zobaczyć, jeśli pełnym zdaniem zostało wyrenderowane w odpowiedniej kolejności programu word.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 Element <xref:System.Threading.Barrier> jest obiektem, który uniemożliwia poszczególne zadania w operacji równoległej z dalszego barierę aż wszystkie zadania. Jest to przydatne, gdy operacji równoległej odbywa się w fazach, a każda faza wymaga synchronizacji między zadaniami. W tym przykładzie istnieją dwie fazy, aby wykonać operację. W pierwszej fazie każdego zadania wypełnia sekcji buforu z danymi. Po zakończeniu każdego zadania wypełnianie swojego zadania sygnalizuje bariery, które ma być kontynuowana, a następnie czeka. Gdy wszystkie zadania zostały zasygnalizowane barierę, są one odblokowane i rozpoczyna się w drugim etapie. Bariera to konieczne, ponieważ drugi etap wymaga, że każde zadanie podrzędne mają dostęp do wszystkich danych, który został wygenerowany z tym punktem. Bez barierze pierwszego zadania do wykonania może próbować odczytywać buforów, które nie zostały wypełnione jeszcze przez inne zadania. Możliwe jest zsynchronizowanie dowolną liczbę etapów w ten sposób.  
  
## <a name="see-also"></a>Zobacz także

- [Struktury danych dla programowania równoległego](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
