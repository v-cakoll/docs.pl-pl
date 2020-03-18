---
title: Bariera
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138147"
---
# <a name="barrier"></a>Bariera

A <xref:System.Threading.Barrier?displayProperty=nameWithType> jest prymitywem synchronizacji, który umożliwia wiele wątków (znany jako *uczestnicy)* do pracy jednocześnie na algorytm w fazach. Każdy uczestnik wykonuje, dopóki nie osiągnie punkt bariery w kodzie. Bariera stanowi koniec jednego etapu prac. Gdy uczestnik osiągnie barierę, blokuje się, aż wszyscy uczestnicy osiągną tę samą barierę. Po osiągnięciu bariery wszyscy uczestnicy mogą opcjonalnie wywołać akcję pofazie. Ta akcja po fazie może służyć do wykonywania akcji przez jeden wątek, podczas gdy wszystkie inne wątki są nadal blokowane. Po wykonaniu akcji wszyscy uczestnicy zostają odblokowani.  
  
 Poniższy fragment kodu pokazuje podstawowy wzorzec bariery.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Aby uzyskać pełny przykład, zobacz [Jak: synchronizować równoczesnych operacji z barierą](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Dodawanie i usuwanie uczestników

 Podczas tworzenia <xref:System.Threading.Barrier> wystąpienia określ liczbę uczestników. W dowolnym momencie można również dynamicznie dodawać lub usuwać uczestników. Na przykład jeśli jeden uczestnik rozwiązuje jego część problemu, można przechowywać wynik, zatrzymać <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> wykonanie w tym wątku i wywołać, aby zdeterminować liczbę uczestników w barierze. Po dodaniu uczestnika <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>przez wywołanie , wartość zwracana określa bieżący numer fazy, co może być przydatne w celu zainicjowania pracy nowego uczestnika.  
  
## <a name="broken-barriers"></a>Złamane bariery

 Zakleszczenia mogą wystąpić, jeśli jeden uczestnik nie osiągnie bariery. Aby uniknąć tych zakleszczeń, należy <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> użyć przeciążenia metody, aby określić okres przekroczenia czasu i token anulowania. Te przeciążenia zwracają wartość logiczną, którą każdy uczestnik może sprawdzić, zanim przejdzie do następnej fazy.  
  
## <a name="post-phase-exceptions"></a>Wyjątki pofazie

 Jeśli delegat po fazie zgłasza wyjątek, jest opakowany <xref:System.Threading.BarrierPostPhaseException> w obiekt, który jest następnie propagowane do wszystkich uczestników.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariera kontra ContinueWhenAll

 Bariery są szczególnie przydatne, gdy wątki wykonują wiele faz w pętlach. Jeśli kod wymaga tylko jednej lub dwóch faz pracy, należy rozważyć, czy używać <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów z wszelkiego rodzaju niejawne sprzężenia, w tym:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Aby uzyskać więcej informacji, zobacz [Łączenie zadań przy użyciu zadań kontynuacji](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Jak: synchronizować równoczesne operacje z barierą](how-to-synchronize-concurrent-operations-with-a-barrier.md)
