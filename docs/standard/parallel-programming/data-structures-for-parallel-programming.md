---
title: Struktury danych dla Programowania równoległego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: a2271feae78100940b4ecac3c42c9bfefa7e1769
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123150"
---
# <a name="data-structures-for-parallel-programming"></a>Struktury danych dla Programowania równoległego
W .NET Framework w wersji 4 wprowadzono kilka nowych typów, które są przydatne w programowaniu równoległym, w tym zestaw klas kolekcji współbieżnych, typy pierwotne synchronizacji uproszczonej i typów dla inicjowania z opóźnieniem. Można używać tych typów z dowolnym kodem aplikacji wielowątkowych, w tym biblioteką równoległą zadań i PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Klasy kolekcji współbieżnych  
 Klasy kolekcji w przestrzeni nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType> zapewniają bezpieczne dla wątków operacje dodawania i usuwania, które zapobiegają zablokowaniu, gdy jest to możliwe, i używać blokowania szczegółowego, w którym blokady są wymagane. W przeciwieństwie do kolekcji, które zostały wprowadzone w .NET Framework wersje 1,0 i 2,0, Klasa kolekcji współbieżnej nie wymaga, aby kod użytkownika miał jakiekolwiek blokady, gdy uzyskuje dostęp do elementów. Klasy kolekcji współbieżnych mogą znacząco poprawić wydajność nad typami, takimi jak <xref:System.Collections.ArrayList?displayProperty=nameWithType> i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (z blokowaniem wdrożonym przez użytkownika) w scenariuszach, w których wiele wątków dodaje i usuwa elementy z kolekcji.  
  
 W poniższej tabeli wymieniono nowe klasy kolekcji współbieżnych:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Oferuje funkcje blokowania i ograniczania dla kolekcji bezpiecznych dla wątków, które implementują <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Wątki producentów blokują, jeśli nie są dostępne żadne gniazda, lub jeśli kolekcja jest pełna. Wątki odbiorcy blokują, jeśli kolekcja jest pusta. Ten typ obsługuje również dostęp bez blokowania dla odbiorców i producentów. <xref:System.Collections.Concurrent.BlockingCollection%601> może być używana jako klasa bazowa lub magazyn zapasowy w celu zapewnienia blokowania i ograniczania dla dowolnej klasy kolekcji, która obsługuje <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementacja bezpiecznego zbioru wątków, która udostępnia skalowalne operacje dodawania i pobierania.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Typ słownika współbieżne i skalowalne.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Współbieżna i skalowalna Kolejka FIFO.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Współbieżny i skalowalny stos LIFO.|  
  
 Aby uzyskać więcej informacji, zobacz [kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Elementy pierwotne synchronizacji  
 Nowe elementy pierwotne synchronizacji w przestrzeni nazw <xref:System.Threading?displayProperty=nameWithType> umożliwiają precyzyjne i szybsze działanie, unikając kosztownych mechanizmów blokowania znalezionych w starszej wersji kodu wielowątkowości. Niektóre z nowych typów, takich jak <xref:System.Threading.Barrier?displayProperty=nameWithType> i <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> nie mają odpowiedników we wcześniejszych wersjach .NET Framework.  
  
 W poniższej tabeli wymieniono nowe typy synchronizacji:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umożliwia wielu wątkom równoczesne współpracujenie z algorytmem, dostarczając punkt, w którym każde zadanie może sygnalizować jego przybycie, a następnie zablokować do momentu otrzymania niektórych lub wszystkich zadań. Aby uzyskać więcej informacji, zobacz [bariera](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Upraszcza scenariusze tworzenia rozwidlenia i sprzężeń, zapewniając łatwy termin. Aby uzyskać więcej informacji, zobacz [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Typ pierwotny synchronizacji podobny do <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim> jest jaśniejsza, ale może być używany tylko w przypadku komunikacji wewnątrz procesu.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Pierwotna synchronizacja, która ogranicza liczbę wątków, które mogą jednocześnie uzyskiwać dostęp do zasobu lub puli zasobów. Aby uzyskać więcej informacji, zobacz [Semafor i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Element pierwotny blokady wykluczeń, który powoduje, że wątek, który próbuje uzyskać blokadę, czeka w pętli lub *obracał*przez pewien czas przed uzyskaniem jego Quantum. W scenariuszach, w których oczekiwany jest krótki czas oczekiwania na blokadę, <xref:System.Threading.SpinLock> oferuje lepszą wydajność niż inne formy blokowania. Aby uzyskać więcej informacji, zobacz [struktury spinlock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Mały, lekki typ, który pozostanie w określonym czasie i ostatecznie umieści wątek w stanie oczekiwania w przypadku przekroczenia liczby obrotów.  Aby uzyskać więcej informacji, zobacz [metody SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: używanie struktury SpinLock do synchronizacji niskiego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Instrukcje: synchronizowanie operacji współbieżnych z barierą](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Klasy inicjacji z opóźnieniem  
 Po zainicjowaniu z opóźnieniem pamięć dla obiektu nie jest przypisana do momentu, gdy jest to konieczne. Inicjalizacja z opóźnieniem może zwiększyć wydajność dzięki rozproszeniu alokacji obiektów równomiernie przez okres istnienia programu. Możesz włączyć inicjalizację z opóźnieniem dla dowolnego typu niestandardowego, zawijając typ <xref:System.Lazy%601>.  
  
 Poniższa tabela zawiera listę typów inicjalizacji z opóźnieniem:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Zapewnia uproszczone, bezpieczne inicjalizacje wątków.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Zapewnia wartość zainicjowaną przez opóźnieniem w odniesieniu do wątku, przy czym każdy wątek opóźnieniem wywołanie funkcji inicjującej.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Zawiera metody statyczne, które nie wymagają przydzielenia dedykowanego wystąpienia inicjującego. Zamiast tego używają odwołań, aby upewnić się, że obiekty docelowe zostały zainicjowane w miarę uzyskiwania do nich dostępu.|  
  
 Aby uzyskać więcej informacji, zobacz [Inicjalizacja z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Wyjątki agregujące  
 Typ <xref:System.AggregateException?displayProperty=nameWithType> może służyć do przechwytywania wielu wyjątków, które są zgłaszane współbieżnie w oddzielnych wątkach i zwracają je do wątku przyłączania jako pojedynczy wyjątek. Typy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> oraz PLINQ używają <xref:System.AggregateException> w tym celu. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) i [instrukcje: obsługa wyjątków w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
