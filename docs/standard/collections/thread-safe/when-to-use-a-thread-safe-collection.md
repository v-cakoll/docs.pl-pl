---
title: Kiedy należy używać kolekcji bezpiecznych wątkowo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefa1b52907525059b3403e7eb20542d3b5a5c73
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109985"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kiedy należy używać kolekcji bezpiecznych wątkowo
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Wprowadza pięć nowe typy kolekcji, które są specjalnie przeznaczone do wsparcia wielowątkowych dodawania i usuwania działań. Do zapewnienia bezpieczeństwa wątkowego, te nowe typy użyć różnych rodzajów blokowanie wydajne i mechanizmy bezblokadowe synchronizacji. Synchronizacja obciążenie dodaje się do operacji. Obciążenie zależy od rodzaju synchronizacji, która jest używana, rodzaj operacji, które są wykonywane i innych czynników, takich jak liczba wątków, które próbują jednocześnie uzyskać dostęp do kolekcji.  
  
 W niektórych scenariuszach synchronizacji obciążenie jest niewielki i umożliwia wielowątkowych typu wykonywać znacznie szybciej i skalować znacznie lepsze niż równoważnik bez wątkowo, gdy chronione przez blokadę zewnętrznych. W innych scenariuszach obciążenie może spowodować typu wątków do wykonywania i skalować prawie taki sam lub nawet wolniej niż wersji zewnętrznie zablokowane, nie wątkowo typu.  
  
 Poniższe sekcje zawierają ogólne wytyczne o tym, kiedy używać kolekcji bezpiecznych wątkowo i jego odpowiednik bez wątkowo, która ma blokady użytkownika wokół jego odczytu i zapisu. Ponieważ wydajność będzie zależeć od wielu czynników, wskazówki nie jest określone i nie nadaje się zawsze w każdych okolicznościach. Jeśli wydajność jest bardzo ważne, najlepszym sposobem, aby określić typ kolekcji do użycia jest mierzenie wydajności na podstawie konfiguracji reprezentatywny komputera i ładowania. W tym dokumencie są używane następujące terminy:  
  
 *Scenariusz czystego producent — konsument*  
 Wątek danego, jest dodanie lub usunięcie elementów, ale nie oba.  
  
 *Scenariusz mieszane producent — konsument*  
 Jednym z wątków danej jest równoczesne Dodawanie i usuwanie elementów.  
  
 *Przyspieszenie*  
 Szybsze konsolidatorze wydajności względem innego typu w ten sam scenariusz.  
  
 *Skalowalność*  
 Wzrost wydajności, który jest proporcjonalny do liczby rdzeni na komputerze. Algorytm, który jest skalowany dokonuje szybciej osiem rdzeni niż na dwa rdzenie.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) programu vs. Queue(T)  
 W scenariuszach czystego producent — konsument, gdy czas przetwarzania dla każdego elementu jest bardzo mały (kilka instrukcje), następnie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> oferują korzyści z niewielkim wydajności za pośrednictwem <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> ma blokady zewnętrznych. W tym scenariuszu <xref:System.Collections.Concurrent.ConcurrentQueue%601> sprawdza się najlepiej, gdy umieszcza w kolejce jeden dedykowanym wątku, a jeden dedykowanym wątku cofnąć kolejkowania. Jeśli nie wymuszają tę regułę, następnie <xref:System.Collections.Generic.Queue%601> nawet mogą wykonywać nieznacznie szybsze niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> na komputerach, które mają wiele rdzeni.  
  
 Gdy czas przetwarzania wynosi około 500 FLOPS (operacji zmiennoprzecinkowych) lub więcej, następnie reguła dwóch wątku nie ma zastosowania do <xref:System.Collections.Concurrent.ConcurrentQueue%601>, który następnie jest bardzo dobra skalowalności. <xref:System.Collections.Generic.Queue%601> nie działa dobrze w tym scenariuszu.  
  
 W mieszanym producent — konsument scenariusze, gdy czas przetwarzania jest bardzo mały <xref:System.Collections.Generic.Queue%601> zawierający zewnętrznego blokady skaluje się lepiej niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> jest. Jednak czas przetwarzania po około 500 FLOPS lub dłużej, a następnie <xref:System.Collections.Concurrent.ConcurrentQueue%601> skaluje się lepiej.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack programu vs. Stos  
 W scenariuszach czystego producent — konsument, gdy czas przetwarzania jest bardzo mały, następnie <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> zawierający zewnętrznego blokady prawdopodobnie będzie wykonywać mniej więcej taka sama, za pomocą jednego z dedykowanego wątku wypychania i jeden wątek zdejmowanie dedykowanych. Jednak jako liczba wątków wzrasta, oba typy spowolnić działanie z powodu nasilenie rywalizacji i <xref:System.Collections.Generic.Stack%601> może działać lepiej niż <xref:System.Collections.Concurrent.ConcurrentStack%601>. Gdy czas przetwarzania jest około 500 FLOPS lub więcej, a następnie obu typów skalowania o tej samej stawki.  
  
 W mieszanym producent — konsument scenariuszy <xref:System.Collections.Concurrent.ConcurrentStack%601> jest szybsza w przypadku zarówno małych, jak i dużych obciążeń.  
  
 Korzystanie z <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> i <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> może znacznie przyspieszyć godziny dostępu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary programu vs. Słownik  
 Ogólnie rzecz biorąc, użyj <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> w każdym scenariuszu, gdzie Dodawanie i aktualizowanie kluczy ani wartości, jednocześnie z wielu wątków. W scenariuszach, które obejmują częste aktualizacje i stosunkowo niewielką liczbą odczyty <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zwykle zapewnia niewielkie korzyści. W scenariuszach obejmujących wiele operacji odczytu i wiele aktualizacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ogólnie jest znacznie szybsze, na komputerach z dowolną liczbą rdzeni.  
  
 W scenariuszach obejmujących częste aktualizacje, można zwiększyć stopień współbieżności w <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , a następnie zmierzyć, aby zobaczyć, czy zwiększona wydajność na komputerach, które mają więcej rdzeni. Jeśli zmienisz poziom współbieżności, należy unikać możliwie globalne operacje.  
  
 Jeśli użytkownik jest tylko do odczytu klucza lub wartości, <xref:System.Collections.Generic.Dictionary%602> przebiega szybciej, ponieważ synchronizacja nie jest wymagana, jeśli słownik nie jest modyfikowana przez wszystkie wątki.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 W scenariuszach czystego producent — konsument <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> wykona prawdopodobnie wolniej niż inne typy kolekcji współbieżnych.  
  
 W mieszanym producent — konsument scenariuszy <xref:System.Collections.Concurrent.ConcurrentBag%601> jest zwykle znacznie szybsze i bardziej skalowalne niż każdy inny typ kolekcji współbieżnych dla małych i dużych obciążeń.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Gdy blokujących i ograniczających semantyki są wymagane, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> będzie prawdopodobnie działać szybciej, niż niestandardowych implementacji. Obsługuje również zaawansowane anulowania, wyliczenia i obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)  
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
