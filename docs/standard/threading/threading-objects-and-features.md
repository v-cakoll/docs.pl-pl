---
title: Wątkowość obiektów i funkcji
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128958"
---
# <a name="threading-objects-and-features"></a>Wątkowość obiektów i funkcji

Wraz z <xref:System.Threading.Thread?displayProperty=nameWithType> klasą .NET udostępnia szereg klas, które ułatwiają tworzenie aplikacji wielowątkowych. Następujące artykuły zawierają przegląd tych klas:

|Tytuł|Opis|  
|-----------|-----------------|  
|[Zarządzana pula wątków](the-managed-thread-pool.md)|Opisuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType> klasę, która zapewnia pulę wątków roboczych, które są zarządzane przez .NET.|  
|[Czasomierze](timers.md)|W tym artykule opisano czasomierzy .NET, które mogą być używane w środowisku wielowątkowym.|
|[Przegląd elementów podstawowych synchronizacji](overview-of-synchronization-primitives.md)|W tym artykule opisano typy, które mogą służyć do synchronizowania dostępu do udostępnionego zasobu lub interakcji wątku sterowania.|
|[EventWaitHandle](eventwaithandle.md)|Opisuje <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> klasę, która reprezentuje zdarzenie synchronizacji wątku.|
|[CountdownEvent](countdownevent.md)|Opisuje <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> klasę, która reprezentuje zdarzenie synchronizacji wątku, który staje się ustawiony, gdy jego liczba wynosi zero.|
|[Muteksy](mutexes.md)|Opisuje <xref:System.Threading.Mutex?displayProperty=nameWithType> klasę, która udziela wyłącznego dostępu do zasobu udostępnionego.|
|[Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md)|Opisuje <xref:System.Threading.Semaphore?displayProperty=nameWithType> klasę, która ogranicza liczbę wątków, które mogą uzyskiwać dostęp do zasobu udostępnionego lub puli zasobów jednocześnie.|
|[Bariera](barrier.md)|Opisuje <xref:System.Threading.Barrier?displayProperty=nameWithType> klasę, która implementuje wzorzec bariery dla koordynacji wątków w operacjach etapowych.|
|[SpinLock](spinlock.md)|Opisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturę, która jest lekką alternatywą dla <xref:System.Threading.Monitor?displayProperty=nameWithType> klasy dla niektórych scenariuszy blokowania niskiego poziomu.|
|[SpinWait](spinwait.md)|Opisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturę, która zapewnia obsługę oczekiwania opartego na spin.|

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Używanie wątków i wątkowości](using-threads-and-threading.md)
- [Asynchroniczne We/Wy pliku](../io/asynchronous-file-i-o.md)
- [Programowanie równoległe](../parallel-programming/index.md)
- [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md)
