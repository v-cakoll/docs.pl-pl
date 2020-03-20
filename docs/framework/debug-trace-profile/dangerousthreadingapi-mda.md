---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: d3fe7d11657c2f9edd1fea7ff639f878f993d6b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174774"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
Asystent `dangerousThreadingAPI` debugowania zarządzanego (MDA) jest <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> aktywowany, gdy metoda jest wywoływana w wątku innym niż bieżący wątek.  
  
## <a name="symptoms"></a>Objawy  
 Aplikacja nie odpowiada lub zawiesza się na czas nieokreślony. Dane systemu lub aplikacji mogą być pozostawione w nieprzewidywalnym stanie tymczasowo lub nawet po zamknięciu aplikacji. Niektóre operacje nie są zakończeniu zgodnie z oczekiwaniami.  
  
 Objawy mogą się znacznie różnić ze względu na przypadkowość nieodłącznie związane z problemem.  
  
## <a name="cause"></a>Przyczyna  
 Wątek jest asynchronicznie zawieszone przez <xref:System.Threading.Thread.Suspend%2A> inny wątek przy użyciu metody. Nie ma sposobu, aby określić, kiedy jest bezpiecznie zawiesić inny wątek, który może być w środku operacji. Zawieszenie wątku może spowodować uszkodzenie danych lub złamanie invariants. Jeśli wątek zostanie umieszczony w stanie wstrzymania i nigdy nie zostanie wznowiony przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zawiesić się na czas nieokreślony i ewentualnie uszkodzić dane aplikacji. Metody te zostały oznaczone jako przestarzałe.  
  
 Jeśli prymitywy synchronizacji są utrzymywane przez wątek docelowy, pozostają one przechowywane podczas zawieszenia. Może to prowadzić do zakleszczenia powinien inny <xref:System.Threading.Thread.Suspend%2A>wątek, na przykład wątek wykonywania , próba uzyskania blokady na prymitywne. W tej sytuacji problem objawia się jako zakleszczenie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Unikaj wzorów, które <xref:System.Threading.Thread.Suspend%2A> <xref:System.Threading.Thread.Resume%2A>wymagają użycia i . Do <xref:System.Threading.Monitor>współpracy między wątkami należy użyć ujegłędnych synchronizacji, takich jak , <xref:System.Threading.ReaderWriterLock> <xref:System.Threading.Mutex>, lub C# `lock` instrukcji. Jeśli należy użyć tych metod, zmniejszyć okno czasu i zminimalizować ilość kodu, który wykonuje, gdy wątek jest w stanie wstrzymania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To MDA nie ma wpływu na CLR. Raportuje tylko dane dotyczące niebezpiecznych operacji wątkowania.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA identyfikuje niebezpieczną metodę gwintowania, która spowodowała jej aktywację.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje wywołanie <xref:System.Threading.Thread.Suspend%2A> metody, która `dangerousThreadingAPI`powoduje aktywację .  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [lock — Instrukcja](../../csharp/language-reference/keywords/lock-statement.md)
