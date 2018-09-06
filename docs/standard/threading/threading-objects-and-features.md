---
title: Wątkowość obiektów i funkcji
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039332"
---
# <a name="threading-objects-and-features"></a>Wątkowość obiektów i funkcji

Wraz z <xref:System.Threading.Thread?displayProperty=nameWithType> klasy .NET zapewnia szereg klas, które ułatwiają tworzenie aplikacji wielowątkowych. Poniższe artykuły zawierają omówienie tych klas:

|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzana Pula wątków](the-managed-thread-pool.md)|W tym artykule opisano <xref:System.Threading.ThreadPool?displayProperty=nameWithType> klasy, która dostarcza puli wątków roboczych, które są zarządzane przez platformy .NET.|  
|[Czasomierze](timers.md)|W tym artykule opisano czasomierzy, które mogą być używane w środowisku wielowątkowym.|
|[Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md)|W tym artykule opisano klasy, które mogą służyć do synchronizowania dostępu do danych lub kontrolki interakcji wątku.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|W tym artykule opisano uchwyty oczekiwania na zdarzenie zarządzane, które są używane do synchronizowania działaniach Sygnalizowanie i Oczekiwanie na sygnałów.|
|[Muteksy](mutexes.md)|Opisuje sposób używania <xref:System.Threading.Mutex?displayProperty=nameWithType> do synchronizowania dostępu do obiektu lub tworzyć własne mechanizmy synchronizacji.|
|[Operacje blokowane](interlocked-operations.md)|W tym artykule opisano <xref:System.Threading.Interlocked?displayProperty=nameWithType> klasy, która dostarcza operacji niepodzielnych w przypadku zmiennych, które są współużytkowane przez wiele wątków.|
|[reader_writer_lock, klasa](reader-writer-locks.md)|W tym artykule opisano <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> klasy, która zapewnia semantykę, pojedynczego — moduł zapisujący/wielu czytników.|
|[Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md)|W tym artykule opisano <xref:System.Threading.Semaphore?displayProperty=nameWithType> klasy i wyjaśniono, jak z niej korzystać w celu kontrolowania dostępu do ograniczonych zasobów.|
|[Barrier](barrier.md)|W tym artykule opisano <xref:System.Threading.Barrier?displayProperty=nameWithType> klasę, która implementuje wzorzec barierę koordynacji wątków w operacjach etapowe.|
|[SpinLock](spinlock.md)|W tym artykule opisano <xref:System.Threading.SpinLock?displayProperty=nameWithType> klasy, która jest lekkie alternatywą <xref:System.Threading.Monitor?displayProperty=nameWithType> klasy w niektórych scenariuszach niskiego poziomu.|
|[SpinWait](spinwait.md)|W tym artykule opisano <xref:System.Threading.SpinWait?displayProperty=nameWithType> klasy, która jest elementem niskiego poziomu synchronizacji, który wykonuje rotowania zajętości przed zainicjowaniem oczekiwanie na podstawie jądra.|

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Używanie wątków i wątkowości](using-threads-and-threading.md)
- [Asynchroniczne operacje We/Wy pliku](../io/asynchronous-file-i-o.md)
- [Programowanie równoległe](../parallel-programming/index.md)
- [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)
