---
title: "Struktury danych dla Programowania równoległego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2da3e1ecfb9018adf7827aad6a569cd057c59eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="data-structures-for-parallel-programming"></a>Struktury danych dla Programowania równoległego
.NET Framework w wersji 4 wprowadzono kilka nowych typów, które są przydatne w Programowanie równoległe, w tym zestaw kolekcji współbieżnych klas, elementy podstawowe synchronizacji lekkie i typy dla inicjowania z opóźnieniem. Z kodem aplikacji wielowątkowych, włączając w bibliotece równoległych zadań i PLINQ można używać tych typów.  
  
## <a name="concurrent-collection-classes"></a>Klasy kolekcji współbieżnych  
 Kolekcja klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw zapewnić bezpieczne wątkowo dodawania i usuwania działań, które uniknąć blokad, gdy jest to możliwe oraz użyć szczegółowych blokowania, gdzie blokady są niezbędne. W przeciwieństwie do kolekcji, które zostały wprowadzone w wersji systemu .NET Framework 1.0 i 2.0 klasy kolekcji współbieżnych nie wymaga kod użytkownika zostały wszystkie blokady, gdy uzyskuje dostęp do elementów. Klasy kolekcji współbieżnych może znacznie poprawić wydajność przez typy takich jak <xref:System.Collections.ArrayList?displayProperty=nameWithType> i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (z zaimplementowana użytkownika blokowanie) w scenariuszach, w której wiele wątków Dodawanie i usuwanie elementów z kolekcji.  
  
 W poniższej tabeli wymieniono nowe klasy kolekcji współbieżnych:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Umożliwia blokowanie i ograniczenia możliwości kolekcje bezpieczne wątkowo, które implementują <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Producent wątków zablokować, jeśli nie ma dostępnych miejsc lub jeśli kolekcja jest pełna. Wątki konsumenta zablokować, jeśli kolekcja jest pusta. Ten typ obsługuje również bez blokowania dostępu przez konsumentów i producentów. <xref:System.Collections.Concurrent.BlockingCollection%601>mogą być używane jako klasę podstawową lub magazyn do blokowania i ograniczenia dla każdej klasy kolekcji, która obsługuje zapasowy <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implementację zbioru wątkowo, która oferuje skalowalne Dodaj i operacje pobierania.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Typ równoczesnych i skalowalne słownika.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Kolejka FIFO równoczesnych i skalowalność.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Stos LIFO równoczesnych i skalowalność.|  
  
 Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Elementy podstawowe synchronizacji  
 Nowych elementów podstawowych synchronizacji w <xref:System.Threading?displayProperty=nameWithType> przestrzeni nazw włączenia szczegółowych współbieżności i zwiększyć wydajność, unikając kosztowne mechanizmy blokady w starszej wersji kodu wielowątkowości. Niektóre z nowych typów, takie jak <xref:System.Threading.Barrier?displayProperty=nameWithType> i <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> mieć nie odpowiedników we wcześniejszych wersjach programu .NET Framework.  
  
 W poniższej tabeli wymieniono nowe typy synchronizacji:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Umożliwia wiele wątków do pracy w algorytm równocześnie zapewniając punktu, jaką każdego zadania można zasygnalizować jego a następnie zablokować dopóki niektóre lub wszystkie zadania zostały dostarczone. Aby uzyskać więcej informacji, zobacz [bariery](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Ułatwia rozwidlenia i Dołącz do scenariuszy, zapewniając mechanizm easy spotkania. Aby uzyskać więcej informacji, zobacz [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Podobnie jak podstawowy synchronizacji <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>jest jaśniejszego wagi, ale mogą służyć tylko do komunikacji wewnątrz procesu. Aby uzyskać więcej informacji, zobacz [ManualResetEvent i ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Podstawowy synchronizacji, która ogranicza liczbę wątków, które można jednocześnie uzyskać dostęp do zasobu lub pulę zasobów. Aby uzyskać więcej informacji, zobacz [semafor i klasa SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Podstawowy blokady wzajemne wykluczenie powodujący wątek próbuje uzyskać blokady oczekiwania w pętli, lub *pokrętła*, w danym okresie czasu przed jego quantum produkcji. W scenariuszach, w którym powinien być krótki, oczekiwanie na blokadę <xref:System.Threading.SpinLock> zapewnia większą wydajność niż inne formy blokowania. Aby uzyskać więcej informacji, zobacz [struktury SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Małe, lekkie typu, który będzie pokrętła przez określony czas i po pewnym czasie umieść wątku w stan oczekiwania, po przekroczeniu liczby pokrętła.  Aby uzyskać więcej informacji, zobacz [metody SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Instrukcje: używanie struktury SpinLock do synchronizacji niskiego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Porady: synchronizacja jednoczesnych operacji za pomocą bariery](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Inicjalizacja z opóźnieniem klas  
 Pamięci dla obiekt z Inicjalizacja z opóźnieniem, nie jest przydzielona, dopóki nie jest wymagana. Inicjalizacja z opóźnieniem może poprawić wydajność przez rozłożenie obiekt alokacji równomiernie okres istnienia programu. Inicjalizacja z opóźnieniem dla dowolnego typu niestandardowego można włączyć zawijania typ <xref:System.Lazy%601>.  
  
 Poniższa tabela zawiera listę typów Inicjalizacja z opóźnieniem:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Udostępnia niewielka, obsługującej wielowątkowość Inicjalizacja z opóźnieniem.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Zapewnia wartość opóźnieniem zainicjować na podstawie dla każdego wątku każdy wątek opóźnieniem wywoływania funkcji inicjowania.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Udostępnia metody statyczne, które uniknąć konieczności przydzielić dedykowane wystąpienie Inicjalizacja z opóźnieniem. W zamian użyj ich odwołań do upewnij się, że zainicjowano elementy docelowe, ponieważ są one używane.|  
  
 Aby uzyskać więcej informacji, zobacz [Incjalizacji](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Łączny wyjątków  
 <xref:System.AggregateException?displayProperty=nameWithType> Typu może służyć do przechwytywania wielu wyjątków, które są zgłaszane jednocześnie w oddzielnych wątkach i przywróć ich łącząca wątku pojedynczego wyjątek. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> typów i PLINQ używają <xref:System.AggregateException> często w tym celu. Aby uzyskać więcej informacji, zobacz [NIB: porady: obsługa wyjątków zgłaszanych przez zadania](http://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d) i [porady: obsługi wyjątków w zapytaniu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
