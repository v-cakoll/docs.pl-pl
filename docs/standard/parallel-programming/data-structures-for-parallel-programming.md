---
title: Struktury danych dla Programowania równoległego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: a2271feae78100940b4ecac3c42c9bfefa7e1769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123150"
---
# <a name="data-structures-for-parallel-programming"></a>Struktury danych dla Programowania równoległego
.NET Framework wersja 4 wprowadza kilka nowych typów, które są przydatne w programowaniu równoległym, w tym zestaw klas kolekcji równoczesnych, ldyty synchronizacji lekkich i typy dla inicjowania z opóźnieniem. Można użyć tych typów z dowolnym wielowątkowym kodem aplikacji, w tym biblioteką równoległą zadania i plinq.  
  
## <a name="concurrent-collection-classes"></a>Klasy kolekcji równoczesnych  
 Klasy kolekcji w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw zapewniają operacje dodawania i usuwania bezpiecznego dla wątków, które unikają blokad, gdy jest to możliwe, i używają blokad drobnoziarnistych, gdy konieczne są blokady. W przeciwieństwie do kolekcji, które zostały wprowadzone w .NET Framework w wersjach 1.0 i 2.0, klasa kolekcji równoczesnych nie wymaga kodu użytkownika do podjęcia żadnych blokad, gdy uzyskuje dostęp do elementów. Klasy kolekcji równoczesnych może znacznie zwiększyć <xref:System.Collections.ArrayList?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> wydajność w stosunku do typów, takich jak i (z blokady implementowane przez użytkownika) w scenariuszach, w których wiele wątków dodać i usunąć elementy z kolekcji.  
  
 W poniższej tabeli wymieniono nowe klasy kolekcji równoczesnych:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Zapewnia możliwości blokowania i ograniczające dla kolekcji <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>bezpiecznych dla wątków, które implementują . Wątki producenta blokują, jeśli nie są dostępne szczeliny lub jeśli kolekcja jest pełna. Blok wątków konsumenckich, jeśli kolekcja jest pusta. Ten typ obsługuje również nieblokujący dostęp konsumentów i producentów. <xref:System.Collections.Concurrent.BlockingCollection%601>może służyć jako klasy podstawowej lub magazynu zapasowego, aby zapewnić <xref:System.Collections.Generic.IEnumerable%601>blokowanie i ograniczanie dla każdej klasy kolekcji, która obsługuje .|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementacja worka bezpiecznego dla wątków, która zapewnia skalowalne dodawanie i wykonywanie operacji.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Współbieżny i skalowalny typ słownika.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Jednoczesna i skalowalna kolejka FIFO.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Równoczesny i skalowalny stos LIFO.|  
  
 Aby uzyskać więcej informacji, zobacz [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Prymitywy synchronizacji  
 Nowe elementy pierwotne synchronizacji w <xref:System.Threading?displayProperty=nameWithType> przestrzeni nazw umożliwiają konwencyjną drobnoziarnistą i szybszą wydajność, unikając kosztownych mechanizmów blokowania znalezionych w starszym kodzie wielowątkowym. Niektóre z nowych typów, <xref:System.Threading.Barrier?displayProperty=nameWithType> <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> takich jak i nie mają odpowiedników we wcześniejszych wersjach .NET Framework.  
  
 W poniższej tabeli wymieniono nowe typy synchronizacji:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umożliwia wiele wątków do pracy na algorytm równolegle, zapewniając punkt, w którym każde zadanie może sygnalizować jego przybycie, a następnie zablokować, dopóki niektóre lub wszystkie zadania nie przybył. Aby uzyskać więcej informacji, zobacz [Barrier](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Upraszcza scenariusze rozwidliwości i łączenia, zapewniając łatwy mechanizm spotkania. Aby uzyskać więcej informacji, zobacz [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Prymityw synchronizacji <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>podobny do . <xref:System.Threading.ManualResetEventSlim>jest lżejszy, ale może być używany tylko do komunikacji wewnątrzprocesowej.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Prymityw synchronizacji, który ogranicza liczbę wątków, które mogą jednocześnie uzyskać dostęp do zasobu lub puli zasobów. Aby uzyskać więcej informacji, zobacz [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Wzajemne wykluczenie blokady prymitywne, które powoduje, że wątek, który próbuje uzyskać blokady czekać w pętli, lub *spin*, przez okres czasu przed uzyskaniem jego kwantowej. W scenariuszach, w których oczekuje się, <xref:System.Threading.SpinLock> że oczekiwanie na blokadę będzie krótkie, oferuje lepszą wydajność niż inne formy blokowania. Aby uzyskać więcej informacji, zobacz [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Mały, lekki typ, który będzie obracać się przez określony czas i ostatecznie umieścić wątek w stanie oczekiwania, jeśli liczba obrotów zostanie przekroczona.  Aby uzyskać więcej informacji, zobacz [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: używanie struktury SpinLock do synchronizacji niskiego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Jak: Synchronizować równoczesne operacje z barierą](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Powolne klasy inicjalizacji  
 W przypadku inicjowania z opóźnieniem pamięć dla obiektu nie jest przydzielana, dopóki nie jest potrzebna. Inicjowanie z opóźnieniem może zwiększyć wydajność przez rozłożenie alokacji obiektów równomiernie przez cały okres istnienia programu. Można włączyć inicjowanie z opóźnieniem dla <xref:System.Lazy%601>dowolnego typu niestandardowego, zawijając typ .  
  
 W poniższej tabeli wymieniono typy inicjowania z opóźnieniem:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Zapewnia lekkie, bezpieczne dla wątków inicjalizacji leniwe.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Zapewnia leniwie zainicjowaną wartość na podstawie dla poszczególnych wątków, z każdym wątku leniwie wywołując funkcję inicjowania.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Zapewnia metody statyczne, które uniknąć konieczności przydzielenia dedykowane, opóźnienie inicjowania wystąpienia. Zamiast tego używają odwołań, aby upewnić się, że obiekty docelowe zostały zainicjowane podczas uzyskiwania do nich dostępu.|  
  
 Aby uzyskać więcej informacji, zobacz [Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Wyjątki agregowane  
 Typ <xref:System.AggregateException?displayProperty=nameWithType> może służyć do przechwytywania wielu wyjątków, które są generowane jednocześnie w oddzielnych wątków i zwrócić je do wątku łączącego jako pojedynczy wyjątek. I <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> rodzaje i PLINQ szeroko wykorzystać <xref:System.AggregateException> do tego celu. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) i [jak: Obsługa wyjątków w kwerendzie PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
