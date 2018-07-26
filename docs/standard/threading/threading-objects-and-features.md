---
title: Wątkowość obiektów i funkcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d689aeb91ad79b776c3b93c1809ec46947ea60b
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874790"
---
# <a name="threading-objects-and-features"></a>Wątkowość obiektów i funkcji
.NET Framework oferuje pewną liczbę obiektów, które ułatwiają tworzenie i zarządzanie nimi aplikacji wielowątkowych. Zarządzane wątki są reprezentowane przez <xref:System.Threading.Thread> klasy. <xref:System.Threading.ThreadPool> Klasa oferuje łatwe tworzenie i zarządzanie zadania w tle wielowątkowych. <xref:System.ComponentModel.BackgroundWorker> Klasy jest taka sama dla zadania, które współdziałają z interfejsem użytkownika. <xref:System.Threading.Timer> Klasy wykonuje zadania w tle w określonych interwałach.  
  
 Ponadto, istnieje kilka klas, które synchronizują działania wątków, w tym <xref:System.Threading.Semaphore> i <xref:System.Threading.EventWaitHandle> klasy wprowadzone w programie .NET Framework w wersji 2.0. Porównanie funkcji w ramach tych zajęć [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzana pula wątków](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Wyjaśnia **ThreadPool** klasy, która pozwala na żądanie wątku w celu wykonania zadania bez konieczności zarządzania dowolnego wątku samodzielnie.  
  
 [Czasomierze](../../../docs/standard/threading/timers.md)  
 W tym artykule opisano czasomierzy, które mogą być używane w środowisku wielowątkowym.  
  
 [Monitory](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Opis sposobu użycia **Monitor** klasy do synchronizowania dostępu do elementu członkowskiego lub tworzyć własne wątku typy zarządzania.  
  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 W tym artykule opisano <xref:System.Threading.WaitHandle> klasy, abstrakcyjna klasa bazowa dla zdarzeń oczekiwania dojść, muteksy i semaforów, dzięki czemu oczekiwanie na wiele zdarzeń synchronizacji.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 W tym artykule opisano uchwyty oczekiwania na zdarzenie zarządzane, które są używane do synchronizowania działaniach Sygnalizowanie i Oczekiwanie na sygnałów.  
  
 [Muteksy](../../../docs/standard/threading/mutexes.md)  
 Opis sposobu użycia <xref:System.Threading.Mutex> do synchronizowania dostępu do obiektu lub tworzyć własne mechanizmy synchronizacji.  
  
 [Operacje blokowane](../../../docs/standard/threading/interlocked-operations.md)  
 Opis sposobu użycia <xref:System.Threading.Interlocked> klasy, aby zwiększyć lub zmniejszyć wartość i przechowuj wartość w jednej niepodzielnej operacji.  
  
 [reader_writer_lock, klasa](../../../docs/standard/threading/reader-writer-locks.md)  
 Definiuje blokady, który implementuje semantykę pojedynczego — moduł zapisujący/wielu czytników.  
  
 [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 W tym artykule opisano <xref:System.Threading.Semaphore> obiektów i wyjaśniono, jak ich używać do kontrolowania dostępu do ograniczonych zasobów.  
  
 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Porównanie funkcji blokowania i synchronizacja wątków zarządzanych klas .NET Framework.  
  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 W tym artykule opisano <xref:System.Threading.Barrier> obiekty, które implementują wzorzec barierę koordynacji wątków w operacjach etapowe.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 W tym artykule opisano <xref:System.Threading.SpinLock>, uproszczone alternatywa klasa monitora w niektórych scenariuszach niskiego poziomu.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 W tym artykule opisano <xref:System.Threading.SpinWait>, podstawowego synchronizacji na niskim poziomie, który wykonuje rotowania zajętości przed zainicjowaniem oczekiwanie na podstawie jądra.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Threading.Thread>  
 Zawiera dokumentację referencyjną dla **wątku** klasy, która reprezentuje wątków zarządzanych, czy pochodzi z niezarządzanego kodu, czy został utworzony w zarządzanej aplikacji.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Umożliwia zadania w tle, które współdziałają z interfejsem użytkownika, komunikacji za pośrednictwem zdarzeń zgłaszanych w wątku interfejsu użytkownika.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Opis sposobu asynchronicznych operacji We/Wy portów użyciu puli wątków wymagają przetwarzania tylko wtedy, gdy zakończeniu operacji wejścia/wyjścia.  
  
 [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 W tym artykule opisano zalecane podejście do programowania wielowątkowe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i nowszych.
