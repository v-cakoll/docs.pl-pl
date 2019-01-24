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
ms.openlocfilehash: 3cfbc1439be457987c058ee6d0298e93aa37f5d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716016"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI` Zarządzanego Asystenta debugowania (MDA) jest aktywowany po <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda jest wywoływana z wątku innego niż bieżący wątek.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja nie odpowiada lub zawiesza się na czas nieokreślony. Dane systemu lub aplikacji może pozostać w nieprzewidywalnym stanie tymczasowo, lub nawet po zakończeniu zamknij aplikację. Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.  
  
 Objawy mogą się znacznie zmieniać z powodu losowości związane z problemem.  
  
## <a name="cause"></a>Przyczyna  
 Wątek asynchronicznie została zawieszona przez inny wątek przy użyciu <xref:System.Threading.Thread.Suspend%2A> metody. Nie istnieje żaden sposób, aby określić, kiedy jest bezpieczne wstrzymania innego wątku, która może być w trakcie wykonywania operacji. Zawieszanie wątków może spowodować uszkodzenie danych lub dzieleniu invariants. Wątek będzie umieszczona w stanie wstrzymania i wznowienia nigdy nie przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikację można odłożyć na czas nieokreślony i potencjalnie uszkodzić dane aplikacji. Tych metod oznaczono jako przestarzałe.  
  
 Jeśli podstawowych synchronizacji są przechowywane przez wątek docelowy, pozostaną one konsekwencje na gruncie podczas zawieszenia. Może to prowadzić do zakleszczenia powinien innego wątku, na przykład wątek wykonywania <xref:System.Threading.Thread.Suspend%2A>, próba uzyskania blokady na element pierwotny. W takiej sytuacji problem w sytuacji, jak zakleszczenia.  
  
## <a name="resolution"></a>Rozwiązanie  
 Unikaj projektów, które korzystają z <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>. Współpracy między wątkami, użyj elementów podstawowych synchronizacji takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, lub C# `lock` instrukcji. Jeśli musisz użyć następujących metod, przedział czasu i minimalizując zakres ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o niebezpieczne operacje na wątkach.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA identyfikuje niebezpiecznych metodę wątkowości, który spowodował zostanie uaktywniony.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje wywołanie <xref:System.Threading.Thread.Suspend%2A> metodę, która powoduje, że aktywacja `dangerousThreadingAPI`.  
  
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
- [lock, instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md)
