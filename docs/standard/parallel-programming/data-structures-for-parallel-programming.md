---
title: Struktury danych dla Programowania równoległego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eb79aaf1f207d8d5ec175f32dc9a47170d604f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973397"
---
# <a name="data-structures-for-parallel-programming"></a>Struktury danych dla Programowania równoległego
.NET Framework w wersji 4 wprowadza kilka nowych typów, które są przydatne do programowania równoległego, w tym zestaw klas kolekcji współbieżnych, podstawowych uproszczone synchronizacji i typów d inicjowania z opóźnieniem. Można użyć tych typów, zawierające kod aplikacji wielowątkowych, w tym w bibliotece równoległych zadań i PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Klas kolekcji współbieżnych  
 Kolekcja klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw podać metodą o bezpiecznych wątkach dodawania i usuwania operacji, które uniknąć blokad, tam gdzie to możliwe oraz Użyj blokowanie szczegółowe, gdzie blokady są niezbędne. W przeciwieństwie do kolekcji, które zostały wprowadzone w .NET Framework w wersji 1.0 i 2.0 klasy kolekcji współbieżnych nie wymaga kod użytkownika do podejmowania żadnych blokad, gdy uzyskuje dostęp do elementów. Klasy kolekcji współbieżnych może znacznie poprawić wydajność przez typy takie jak <xref:System.Collections.ArrayList?displayProperty=nameWithType> i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (z blokowanie zaimplementowane przez użytkownika) w scenariuszach, gdzie Dodawanie i usuwanie elementów z kolekcji w wielu wątkach.  
  
 Poniższa tabela zawiera listę nowych klas kolekcji współbieżnych:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Zapewnia blokowania i ograniczenia możliwości kolekcje obsługujące wielowątkowość, które implementują <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Wątki producenta zablokować, jeśli nie ma dostępnych miejsc, lub jeśli kolekcja jest pełna. Wątki konsumenta zablokować, jeśli kolekcja jest pusta. Ten typ obsługuje również nieblokującej na poziomie dostępu przez konsumentów i producentów. <xref:System.Collections.Concurrent.BlockingCollection%601> może służyć jako klasę bazową lub magazyn, aby zapewnić blokowanie i blokujących dla każdej klasy kolekcji, która obsługuje zapasowy <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementację zbiór metodą o bezpiecznych wątkach, która oferuje skalowalne, dodać i operacjami pobierania.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Typ słownika równocześnie i skalowalne.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Kolejki FIFO równocześnie i skalowalne.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Stosu LIFO równocześnie i skalowalne.|  
  
 Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Podstawowych synchronizacji  
 Nowych elementów podstawowych synchronizacji, w <xref:System.Threading?displayProperty=nameWithType> przestrzeni nazw Włącz współbieżność szczegółową i zwiększyć wydajność dzięki unikaniu kosztownych mechanizmy blokady w starszej wersji kodu wielowątkowości. Niektóre z nowych typów, takich jak <xref:System.Threading.Barrier?displayProperty=nameWithType> i <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> mają nie odpowiedniki we wcześniejszych wersjach programu .NET Framework.  
  
 Poniższa tabela zawiera listę nowych typów synchronizacji:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umożliwia wielu wątków do pracy nad algorytmu równoległego, podając punkt, w której każde zadanie podrzędne może sygnalizują jego następnie blokowane, aż już korzystać z niektórych lub wszystkich zadań. Aby uzyskać więcej informacji, zobacz [barierę](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Upraszcza scenariusze rozwidlenia i sprzężenia, dostarczając mechanizmu łatwego spotkania. Aby uzyskać więcej informacji, zobacz [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Element synchronizacji, podobnie jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim> to lekki, ale można używać tylko do komunikacji wewnątrz procesu.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Element synchronizacji, która ogranicza liczbę wątków, które można jednocześnie uzyskać dostęp do zasobu lub puli zasobów. Aby uzyskać więcej informacji, zobacz [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Podstawowego blokady wzajemne wykluczenie, który powoduje wątku, który próbuje uzyskać blokady oczekiwać w pętli, lub *pokrętła*, okres czasu przed jego quantum reaguje. W scenariuszach, w którym powinien być krótki, czas oczekiwania na blokadę <xref:System.Threading.SpinLock> zapewnia większą wydajność niż inne formy blokowania. Aby uzyskać więcej informacji, zobacz [struktury SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Małe, lekkie typ, który będzie pokrętła przez określony czas i ostatecznie umieścić wątku w stan oczekiwania, po przekroczeniu liczby pokrętła.  Aby uzyskać więcej informacji, zobacz [metody SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: Używanie struktury SpinLock do synchronizacji niskiego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Instrukcje: Synchronizacja jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Inicjalizacja z opóźnieniem klas  
 Przy użyciu inicjowania z opóźnieniem pamięci dla obiektu nie jest przydzielony, dopóki nie jest to konieczne. Inicjalizacja z opóźnieniem może zwiększyć wydajność przez rozłożenie przydziały obiektów równomiernie na okres istnienia programu. Można włączyć inicjowania z opóźnieniem dla dowolnego typu niestandardowego przez opakowywanie typ <xref:System.Lazy%601>.  
  
 Poniższa tabela zawiera listę typów inicjowania z opóźnieniem:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Udostępnia lekki, wątkowo inicjowania z opóźnieniem —.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Zapewnia wartość opóźnieniem zainicjowana na zasadzie na wątek, każdy wątek opóźnieniem wywoływania funkcji inicjowania.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Udostępnia metody statyczne, które uniknąć konieczności przydzielić dedykowane wystąpienie inicjowania z opóźnieniem. Zamiast tego używają odwołań, aby upewnić się, że elementy docelowe zostały zainicjowane, ponieważ są one używane.|  
  
 Aby uzyskać więcej informacji, zobacz [inicjowania z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Wyjątki agregacji  
 <xref:System.AggregateException?displayProperty=nameWithType> Typ może być używany do przechwytywania wielu wyjątków, które są zgłaszane jednocześnie w oddzielnych wątkach i przywrócić je do sąsiadującego wątku pojedynczego wyjątek. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> typów i PLINQ używać <xref:System.AggregateException> często w tym celu. Aby uzyskać więcej informacji, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) i [jak: Obsługa wyjątków w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
