---
title: dangerousThreadingAPI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a84fd957800f0cedcd92b36929721b4d0d51b7fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda jest wywoływana w wątku innego niż bieżący wątek.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacja nie odpowiada lub zawiesza się przez nieograniczony czas. Dane systemu lub aplikacji może pozostać w nieprzewidywalnym stanie tymczasowo lub nawet po zamknięciu aplikacji. Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.  
  
 Objawy różnią może z powodu problemu związanego z używaniem losowości.  
  
## <a name="cause"></a>Przyczyna  
 Wątek asynchronicznie został wstrzymany za pomocą innego wątku <xref:System.Threading.Thread.Suspend%2A> metody. Brak nie można określić, kiedy jest bezpieczne zawiesić inny wątek, która może być w trakcie wykonywania operacji. Zawieszanie wątków może spowodować uszkodzenie danych lub dzieleniu invariants. Należy umieścić wątku w stanie wstrzymania i wznowienia nigdy nie przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zostać zawieszona na nieograniczony czas i potencjalnie uszkodzić dane aplikacji. Te metody oznaczono jako przestarzały.  
  
 Jeśli elementy podstawowe synchronizacji są przechowywane przez wątek docelowy, pozostaną one przechowywanych podczas zawieszenia. Może to prowadzić do zakleszczenia powinien innego wątku, na przykład wątku wykonywania <xref:System.Threading.Thread.Suspend%2A>, próba uzyskania blokady na element pierwotny. W takiej sytuacji problem sam się uwidacznia zakleszczenie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Unikaj projekty, które wymagają użycia <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A>. Współpracy między wątkami, użyj takiego jak elementy podstawowe synchronizacji <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, C# lub `lock` instrukcji. Jeśli jest konieczne korzystanie z tych metod, zmniejsza okno czasu i zminimalizować ilość kodu, który wykonuje, gdy wątek jest w stanie wstrzymania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Zwraca tylko dane o niebezpieczne operacje na wątkach.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA identyfikuje niebezpiecznych metodę wątków, który spowodował jej uruchomienia.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje wywołanie <xref:System.Threading.Thread.Suspend%2A> metodę, która powoduje, że aktywacji `dangerousThreadingAPI`.  
  
```  
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
 <xref:System.Threading.Thread>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Lock — instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md)
