---
title: Bariera (.NET Framework)
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a>Bariera (.NET Framework)
A *bariery* jest zdefiniowane przez użytkownika prymitywu synchronizacji, który umożliwia wiele wątków (nazywane *uczestników*) nad jednocześnie algorytm w fazach. Uczestnik wykonuje, dopóki nie osiągnie punkt bariery w kodzie. Bariera reprezentuje koniec jedną fazą pracy. Gdy uczestnika osiągnie bariery, blokuje aż do osiągnięcia wszystkich uczestników ma tego samego bariery. Po wszystkich uczestników osiągnęły bariery, opcjonalnie można wywołać akcję po fazie. Ta faza po akcja może zostać użyta do wykonania akcji przez pojedynczy wątek, podczas gdy inne wątki nadal są zablokowane. Po wykonaniu akcji, uczestników są wszystkie odblokowane.  
  
 Poniższy fragment kodu przedstawia wzorzec bariery podstawowe.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Pełny przykład, zobacz [porady: synchronizowanie jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Dodawanie i usuwanie uczestników  
 Po utworzeniu <xref:System.Threading.Barrier>, określ liczbę uczestników. Można dodać lub usunąć uczestników dynamicznie w dowolnym momencie. Na przykład, jeśli jednego uczestnika rozwiązuje jego część problemu, można przechowywać wynik, Zatrzymaj wykonywanie na wątku i Wywołaj <xref:System.Threading.Barrier.RemoveParticipant%2A> Aby zmniejszyć liczbę uczestników bariera. Po dodaniu uczestnika przez wywołanie metody <xref:System.Threading.Barrier.AddParticipant%2A>, zwracana wartość Określa numer Bieżąca faza, które mogą być przydatne w celu zainicjowania pracy nowego uczestnika.  
  
## <a name="broken-barriers"></a>Przerwane bariery  
 Zakleszczenie może wystąpić, jeśli jednego uczestnika nie może uzyskać dostęp do zapory. Aby uniknąć tych zakleszczenia, użyj przeciążeń <xref:System.Threading.Barrier.SignalAndWait%2A> metodę, aby określić limit czasu i token anulowania. Te zwracane przeciążenia wartość logiczna, która co uczestnika można sprawdzić przed nią nadal do następnej fazy.  
  
## <a name="post-phase-exceptions"></a>Wyjątki po fazie  
 Jeśli delegat po fazie zgłasza wyjątek, jest ujęte w <xref:System.Threading.BarrierPostPhaseException> obiektu, który jest następnie propagowany do wszystkich uczestników.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariera i ContinueWhenAll  
 Bariery są szczególnie przydatne wątków wykonywania faz w pętli. Jeśli kod wymaga tylko jednego lub dwóch faz, należy rozważyć, czy ma być używany <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekty z dowolnego rodzaju niejawne sprzężenia, w tym:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Porady: synchronizacja jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
