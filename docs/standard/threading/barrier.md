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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138147"
---
# <a name="barrier"></a>Bariera

<xref:System.Threading.Barrier?displayProperty=nameWithType> to element pierwotny synchronizacji, który umożliwia wielu wątkom (nazywanym *uczestnikami*) równoczesne działanie na algorytmie w fazach. Każdy uczestnik jest wykonywany do momentu osiągnięcia punktu bariery w kodzie. Bariera reprezentuje koniec jednej fazy pracy. Gdy uczestnik osiągnie barierę, jest blokowany do momentu, aż wszyscy uczestnicy osiągnąli tę samą barierę. Po osiągnięciu bariery przez wszystkich uczestników można opcjonalnie wywołać akcję po fazie. Ta akcja po fazie może służyć do wykonywania akcji przez pojedynczy wątek, gdy wszystkie pozostałe wątki są nadal zablokowane. Po wykonaniu akcji wszystkie osoby nie zostały odblokowane.  
  
 Poniższy fragment kodu przedstawia podstawowy wzorzec bariery.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Pełny przykład można znaleźć w temacie [How to: Synchronizing współbieżnych operacji z barierą](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Dodawanie i usuwanie uczestników

 Podczas tworzenia wystąpienia <xref:System.Threading.Barrier> należy określić liczbę uczestników. Możesz również dynamicznie dodawać i usuwać uczestników w dowolnym momencie. Na przykład jeśli jeden z uczestników rozwiąże swoją część problemu, można przechowywać wyniki, zatrzymać wykonywanie tego wątku i wywoływać <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType>, aby zmniejszyć liczbę uczestników w barierie. Po dodaniu uczestnika przez wywołanie <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, zwracana wartość określa bieżący numer fazy, co może być przydatne w celu zainicjowania pracy nowego uczestnika.  
  
## <a name="broken-barriers"></a>Naruszone bariery

 Zakleszczenie mogą wystąpić, jeśli jeden z uczestników nie osiągnie przeszkody. Aby uniknąć tych zakleszczeń, użyj przeciążeń metody <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType>, aby określić limit czasu i token anulowania. Te przeciążenia zwracają wartość logiczną, którą każdy uczestnik może sprawdzić przed przejściem do kolejnej fazy.  
  
## <a name="post-phase-exceptions"></a>Wyjątki po fazie

 Jeśli delegat po fazie zgłasza wyjątek, jest opakowany w obiekt <xref:System.Threading.BarrierPostPhaseException>, który następnie jest propagowany do wszystkich uczestników.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariera a ContinueWhenAll

 Bariery są szczególnie przydatne, gdy wątki wykonują wiele faz w pętlach. Jeśli kod wymaga tylko jednej lub dwóch faz pracy, należy rozważyć, czy należy używać <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów z dowolnym rodzajem niejawnego sprzężenia, w tym:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Aby uzyskać więcej informacji, zobacz Tworzenie [łańcucha zadań przy użyciu zadań kontynuacji](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Instrukcje: synchronizowanie operacji współbieżnych z barierą](how-to-synchronize-concurrent-operations-with-a-barrier.md)
