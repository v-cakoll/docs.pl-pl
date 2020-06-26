---
title: dangerousThreadingAPI MDA
description: Przejrzyj dangerousThreadingAPI Managed Debug Assistant (MDA), który jest uaktywniany po wywołaniu wątku. Suspend w wątku innym niż bieżący wątek.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416008"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
`dangerousThreadingAPI`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> Metoda jest wywoływana w wątku innym niż bieżący wątek.  
  
## <a name="symptoms"></a>Objawy  
 Aplikacja nie odpowiada lub zawiesza się bez ograniczeń. Dane systemu lub aplikacji mogą być pozostawione w stanie nieprzewidywalnym tymczasowo lub nawet po zamknięciu aplikacji. Niektóre operacje nie są wykonywane zgodnie z oczekiwaniami.  
  
 Objawy mogą się znacznie różnić ze względu na losowość problemu.  
  
## <a name="cause"></a>Przyczyna  
 Wątek jest asynchronicznie zawieszony przez inny wątek przy użyciu <xref:System.Threading.Thread.Suspend%2A> metody. Nie istnieje sposób, aby określić, kiedy jest bezpieczny, aby zawiesić inny wątek, który może znajdować się w środku operacji. Zawieszenie wątku może skutkować uszkodzeniem danych lub przerwaniem niezmiennych. Jeśli wątek ma być umieszczony w stanie wstrzymania i nigdy nie został wznowiony przy użyciu <xref:System.Threading.Thread.Resume%2A> metody, aplikacja może zawiesić się w nieskończoność i prawdopodobnie uszkodzić dane aplikacji. Te metody zostały oznaczone jako przestarzałe.  
  
 Jeśli elementy pierwotne synchronizacji są przechowywane przez wątek docelowy, pozostaną one zachowane podczas zawieszenia. Może to prowadzić do zakleszczenia, na przykład wątek wykonujący <xref:System.Threading.Thread.Suspend%2A> , próbuje uzyskać blokadę dla elementu podstawowego. W tej sytuacji problem występuje w manifeście jako zakleszczenie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Unikaj projektów, które wymagają używania <xref:System.Threading.Thread.Suspend%2A> i <xref:System.Threading.Thread.Resume%2A> . Aby współdziałać między wątkami, należy użyć prymitywów synchronizacji, takich jak <xref:System.Threading.Monitor> , <xref:System.Threading.ReaderWriterLock> , <xref:System.Threading.Mutex> lub instrukcji języka C# `lock` . Jeśli musisz użyć tych metod, Zmniejsz okno czasu i Zminimalizuj ilość kodu, który jest wykonywany, gdy wątek jest w stanie wstrzymania.  
  
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
 Poniższy przykład kodu demonstruje wywołanie <xref:System.Threading.Thread.Suspend%2A> metody, która powoduje aktywację `dangerousThreadingAPI` .  
  
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
- [lock, instrukcja](../../csharp/language-reference/keywords/lock-statement.md)
