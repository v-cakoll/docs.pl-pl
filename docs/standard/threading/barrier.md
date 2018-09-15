---
title: Bariera (.NET Framework)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647554"
---
# <a name="barrier-net-framework"></a>Bariera (.NET Framework)
A *barierę* jest zdefiniowane przez użytkownika synchronizacji, który umożliwia wielu wątków (nazywane *uczestników*) pracować jednocześnie na algorytm w fazach. Każdy uczestnik wykonuje aż do napotkania punktu barierę w kodzie. Bariera oznacza koniec jedną fazą pracy. Gdy uczestnika, który osiągnie barierę, blokuje to, aż wszyscy uczestnicy osiągnęły barierę tego samego. Po wszystkich uczestników osiągnęły barierę, możesz opcjonalnie wywołać akcję po fazie. Tę fazę po okresie akcji może służyć do wykonywania akcji przez pojedynczy wątek, podczas gdy inne wątki nadal są zablokowane. Po wykonaniu akcji uczestnicy są wszystkie odblokowane.  
  
 Poniższy fragment kodu przedstawia wzorzec barierę podstawowe.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Aby uzyskać kompletny przykład, zobacz [porady: synchronizowanie jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Dodawanie i usuwanie uczestników  
 Po utworzeniu <xref:System.Threading.Barrier>, określ liczbę uczestników. Można dodawać lub usuwać uczestników dynamicznie w dowolnym momencie. Na przykład, jeśli jeden uczestnik rozwiązuje jego część problemu, możesz zapisać wynik, Zatrzymaj wykonywanie na wątku, a następnie wywołaj <xref:System.Threading.Barrier.RemoveParticipant%2A> zmniejszyć liczbę uczestników barierę. Po dodaniu uczestnikiem, wywołując <xref:System.Threading.Barrier.AddParticipant%2A>, wartość zwracana określa numer Bieżąca faza, który może być przydatne w celu zainicjowania pracy nowych uczestników.  
  
## <a name="broken-barriers"></a>Przerwane bariery  
 Zakleszczenie może wystąpić, jeśli jednego uczestnika nie uda się połączyć do zapory. Aby uniknąć tych zakleszczenia, użyj przeciążeń <xref:System.Threading.Barrier.SignalAndWait%2A> metodę, aby określić limit czasu i token anulowania. Te przeciążenia, które są zwracane wartość logiczną, każdy uczestnik można sprawdzić przed dalszym przeprowadzenia kolejnej fazy.  
  
## <a name="post-phase-exceptions"></a>Wyjątki po fazie  
 Jeśli delegat po fazie zgłasza wyjątek, jest opakowana w <xref:System.Threading.BarrierPostPhaseException> obiektu, który jest następnie propagowany do wszystkich uczestników.  
  
## <a name="barrier-versus-continuewhenall"></a>Zapory i ContinueWhenAll  
 Bariery są szczególnie przydatne podczas wykonywania wielu faz wątki w pętli. Jeśli kod wymaga tylko jednego lub dwóch faz, rozważ użycie <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiekty z dowolnego rodzaju niejawne łączenia, w tym:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Instrukcje: synchronizacja jednoczesnych operacji za pomocą elementu Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
