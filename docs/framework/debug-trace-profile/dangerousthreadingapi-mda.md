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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d635100c4e8214a7a8659c2d3e4da61825cf243
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966307"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
Asystent debugowania <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> zarządzanego (MDA) jest uaktywniany, gdy metoda jest wywoływana w wątku innym niż bieżący wątek. `dangerousThreadingAPI`  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja nie odpowiada lub zawiesza się bez ograniczeń. Dane systemu lub aplikacji mogą być pozostawione w stanie nieprzewidywalnym tymczasowo lub nawet po zamknięciu aplikacji. Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.  
  
 Objawy mogą się znacznie różnić ze względu na losowość problemu.  
  
## <a name="cause"></a>Przyczyna  
 Wątek jest asynchronicznie zawieszony przez inny wątek przy użyciu <xref:System.Threading.Thread.Suspend%2A> metody. Nie istnieje sposób, aby określić, kiedy jest bezpieczny, aby zawiesić inny wątek, który może znajdować się w środku operacji. Zawieszenie wątku może skutkować uszkodzeniem danych lub przerwaniem niezmiennych. Jeśli wątek ma być umieszczony w stanie wstrzymania i nigdy nie został wznowiony <xref:System.Threading.Thread.Resume%2A> przy użyciu metody, aplikacja może zawiesić się w nieskończoność i prawdopodobnie uszkodzić dane aplikacji. Te metody zostały oznaczone jako przestarzałe.  
  
 Jeśli elementy pierwotne synchronizacji są przechowywane przez wątek docelowy, pozostaną one zachowane podczas zawieszenia. Może to prowadzić do zakleszczenia, na przykład wątek wykonujący <xref:System.Threading.Thread.Suspend%2A>, próbuje uzyskać blokadę dla elementu podstawowego. W tej sytuacji problem występuje w manifeście jako zakleszczenie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Unikaj projektów, które wymagają używania <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>. W celu współpracy między wątkami należy użyć elementów pierwotnych <xref:System.Threading.Monitor>synchronizacji <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>takich jak, C# `lock` ,, lub instrukcji. Jeśli musisz użyć tych metod, Zmniejsz okno czasu i Zminimalizuj ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące niebezpiecznych operacji wątkowości.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA identyfikuje niebezpieczną metodę wątkowości, która spowodowała jej aktywowanie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wywołanie <xref:System.Threading.Thread.Suspend%2A> metody, która powoduje aktywację. `dangerousThreadingAPI`  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [lock, instrukcja](../../csharp/language-reference/keywords/lock-statement.md)
