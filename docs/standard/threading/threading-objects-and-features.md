---
title: Wątkowość obiektów i funkcji
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ba47ece16c74555b58780733e14de9833718c33
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873310"
---
# <a name="threading-objects-and-features"></a>Wątkowość obiektów i funkcji

Wraz z <xref:System.Threading.Thread?displayProperty=nameWithType> klasy .NET zapewnia szereg klas, które ułatwiają tworzenie aplikacji wielowątkowych. Poniższe artykuły zawierają omówienie tych klas:

|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzana Pula wątków](the-managed-thread-pool.md)|W tym artykule opisano <xref:System.Threading.ThreadPool?displayProperty=nameWithType> klasy, która dostarcza puli wątków roboczych, które są zarządzane przez platformy .NET.|  
|[Czasomierze](timers.md)|W tym artykule opisano czasomierzy .NET, które mogą być używane w środowisku wielowątkowym.|
|[Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md)|Opisuje typy, które mogą służyć do synchronizowania dostępu do udostępnionego zasobu lub kontroli wątku interakcji.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|W tym artykule opisano uchwyty oczekiwania na zdarzenie zarządzane, które są używane do synchronizowania działaniach Sygnalizowanie i Oczekiwanie na sygnałów.|
|[Muteksy](mutexes.md)|W tym artykule opisano <xref:System.Threading.Mutex?displayProperty=nameWithType>, która przyznaje wyłącznego dostępu do zasobu udostępnionego.|
|[Operacje blokowane](interlocked-operations.md)|W tym artykule opisano <xref:System.Threading.Interlocked?displayProperty=nameWithType> klasy, która dostarcza operacji niepodzielnych w przypadku zmiennych, które są współużytkowane przez wiele wątków.|
|[reader_writer_lock, klasa](reader-writer-locks.md)|W tym artykule opisano <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> klasy, która zapewnia jedną — moduł zapisujący/wielu czytników dostęp do zasobu udostępnionego.|
|[Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md)|W tym artykule opisano <xref:System.Threading.Semaphore?displayProperty=nameWithType> klasy, która ogranicza liczbę wątków, które mogą uzyskać dostęp do udostępnionego zasobu lub pulę zasobów jednocześnie.|
|[Barrier](barrier.md)|W tym artykule opisano <xref:System.Threading.Barrier?displayProperty=nameWithType> klasę, która implementuje wzorzec barierę koordynacji wątków w operacjach etapowe.|
|[SpinLock](spinlock.md)|W tym artykule opisano <xref:System.Threading.SpinLock?displayProperty=nameWithType> struktury, która jest lekkie alternatywą <xref:System.Threading.Monitor?displayProperty=nameWithType> klasy dla niektórych niskiego poziomu scenariuszy blokowania.|
|[SpinWait](spinwait.md)|W tym artykule opisano <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury, która zapewnia obsługę oczekiwania na podstawie pokrętła.|

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
