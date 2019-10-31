---
title: Wątkowość obiektów i funkcji
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128958"
---
# <a name="threading-objects-and-features"></a>Wątkowość obiektów i funkcji

Wraz z klasą <xref:System.Threading.Thread?displayProperty=nameWithType> platforma .NET udostępnia wiele klas, które ułatwiają tworzenie aplikacji wielowątkowych. W poniższych artykułach przedstawiono przegląd tych klas:

|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzana pula wątków](the-managed-thread-pool.md)|Opisuje klasę <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, która dostarcza pulę wątków roboczych, które są zarządzane przez platformę .NET.|  
|[Czasomierze](timers.md)|Opisuje czasomierze programu .NET, które mogą być używane w środowisku wielowątkowym.|
|[Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md)|Opisuje typy, których można użyć do synchronizowania dostępu do współużytkowanego zasobu lub interakcji wątku kontroli.|
|[EventWaitHandle](eventwaithandle.md)|Opisuje klasę <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, która reprezentuje zdarzenie synchronizacji wątku.|
|[CountdownEvent](countdownevent.md)|Opisuje klasę <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, która reprezentuje zdarzenie synchronizacji wątku, które zostaje ustawione, gdy jego licznik ma wartość zero.|
|[Muteksy](mutexes.md)|Opisuje klasę <xref:System.Threading.Mutex?displayProperty=nameWithType>, która przyznaje wyłączny dostęp do zasobu udostępnionego.|
|[Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md)|Opisuje klasę <xref:System.Threading.Semaphore?displayProperty=nameWithType>, która ogranicza liczbę wątków, które mogą uzyskiwać dostęp do zasobów udostępnionych lub puli zasobów współbieżnie.|
|[Barrier](barrier.md)|Opisuje klasę <xref:System.Threading.Barrier?displayProperty=nameWithType>, która implementuje wzorzec bariery do koordynacji wątków w operacjach stopniowanych.|
|[SpinLock](spinlock.md)|Opisuje strukturę <xref:System.Threading.SpinLock?displayProperty=nameWithType>, która jest lekkim alternatywą dla klasy <xref:System.Threading.Monitor?displayProperty=nameWithType> dla pewnych scenariuszy blokowania niskiego poziomu.|
|[SpinWait](spinwait.md)|Opisuje strukturę <xref:System.Threading.SpinWait?displayProperty=nameWithType>, która zapewnia obsługę czekania na grzbiet.|

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
