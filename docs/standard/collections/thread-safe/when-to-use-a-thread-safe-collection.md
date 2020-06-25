---
title: Kiedy należy używać kolekcji bezpiecznych wątkowo
description: Dowiedz się, kiedy używać kolekcji bezpiecznej dla wątków w programie .NET. Istnieją 5 typów kolekcji, które są specjalnie przeznaczone do obsługi wielowątkowych Dodaj & operacji usuwania.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 499af6d7b8de1decbcffefe0a3b1420cc548488a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85326043"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kiedy używać kolekcji bezpiecznej dla wątków

.NET Framework 4 wprowadził pięć typów kolekcji, które są specjalnie przeznaczone do obsługi operacji dodawania i usuwania wielowątkowych. Aby zapewnić bezpieczeństwo wątków, te typy wykorzystują różne rodzaje wydajnych mechanizmów synchronizacji i blokowania bez blokady. Synchronizacja dodaje narzuty do operacji. Ilość narzutów zależy od rodzaju używanej synchronizacji, rodzaju wykonywanych operacji oraz innych czynników, takich jak liczba wątków, które próbują jednocześnie uzyskać dostęp do kolekcji.  
  
 W niektórych scenariuszach narzuty związane z synchronizacją są nieznaczne i umożliwiają znacznie szybszy i bardziej skalowalne skalowanie, w porównaniu z niebezpiecznym wątkem, w przypadku ochrony przez zewnętrzną blokadę. W innych scenariuszach narzuty mogą spowodować, że typ bezpieczny wątkowo będzie wykonywany i skalowalny na tym samym lub nawet wolniej niż zablokowana zewnętrznie, niezabezpieczona przed wątkiem wersja typu.  
  
 W poniższych sekcjach znajdują się ogólne wskazówki dotyczące sytuacji, w których należy używać kolekcji bezpiecznej dla wątków, a jej bezwzględnie niebezpieczny wątek, która ma blokadę dostarczoną przez użytkownika wokół operacji odczytu i zapisu. Ze względu na to, że wydajność może się różnić w zależności od wielu czynników, wskazówki nie są specyficzne i nie zawsze są ważne we wszystkich okolicznościach. Jeśli wydajność jest bardzo ważna, najlepszym sposobem określenia typu kolekcji, który ma być używany, jest pomiar wydajności na podstawie konfiguracji i obciążeń na reprezentatywnym komputerze. W tym dokumencie są stosowane następujące warunki:  
  
 *Czysty scenariusz dla producentów*\
 Każdy dany wątek dodaje lub usuwa elementy, ale nie oba.  
  
 *Mieszany scenariusz dla klientów*\
 Każdy dany wątek jednocześnie dodaje i usuwa elementy.  
  
 *Przyspieszenie*\
 Szybsza wydajność algorytmu względem innego typu w tym samym scenariuszu.  
  
 *Względem*\
 Zwiększenie wydajności, która jest proporcjonalna do liczby rdzeni na komputerze. Algorytm, który skaluje się szybciej na osiem rdzeni niż w przypadku dwóch rdzeni.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue (T) a kolejka (T)  
 W czystych scenariuszach dla producentów, w których czas przetwarzania dla każdego elementu jest bardzo mały (kilka instrukcji), a następnie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> może oferować niewielkie korzyści z wydajności w porównaniu z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> zewnętrznym zablokowaniem. W tym scenariuszu <xref:System.Collections.Concurrent.ConcurrentQueue%601> najlepiej sprawdza się w przypadku, gdy jeden dedykowany wątek jest kolejką, a jeden dedykowany wątek zostaje cofnięty. Jeśli ta reguła nie jest wymuszana, <xref:System.Collections.Generic.Queue%601> może to być nawet nieco szybsze niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> na komputerach z wieloma rdzeniami.  
  
 Gdy czas przetwarzania ma około 500 FLOPS (operacji zmiennoprzecinkowych) lub więcej, to reguła dwuwątkowa nie ma zastosowania do <xref:System.Collections.Concurrent.ConcurrentQueue%601> , który następnie ma bardzo dobrą skalowalność. <xref:System.Collections.Generic.Queue%601>nie skaluje się dobrze w tym scenariuszu.  
  
 W mieszanych scenariuszach konsumenckich klientów, gdy czas przetwarzania jest bardzo mały, a, <xref:System.Collections.Generic.Queue%601> który ma blokadę zewnętrzną skalowalność <xref:System.Collections.Concurrent.ConcurrentQueue%601> . Jeśli jednak czas przetwarzania ma około 500 FLOPS lub więcej, wówczas <xref:System.Collections.Concurrent.ConcurrentQueue%601> skalowanie jest lepsze.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack a stos  
 W czystych scenariuszach z zakresu producentów, gdy czas przetwarzania jest bardzo mały, a w przypadku, gdy <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> ma ona blokadę zewnętrzną, prawdopodobnie zostanie wykonane o jednym dedykowanym wątku wypychania i jednym dedykowanym wątku usuwanie. Jednak w miarę wzrostu liczby wątków oba typy spowalniają działanie ze względu na zwiększoną rywalizację i <xref:System.Collections.Generic.Stack%601> mogą działać lepiej niż <xref:System.Collections.Concurrent.ConcurrentStack%601> . Gdy czas przetwarzania ma około 500 FLOPS lub więcej, wówczas oba typy skalują o tej samej stawce.  
  
 W mieszanych scenariuszach konsumenckich klientów program <xref:System.Collections.Concurrent.ConcurrentStack%601> jest szybszy dla małych i dużych obciążeń.  
  
 Korzystanie z <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> i <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> może znacznie przyspieszyć czasy dostępu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary a słownik  
 Ogólnie rzecz biorąc, należy użyć <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> w dowolnym scenariuszu, w którym są dodawane i aktualizowane klucze lub wartości jednocześnie z wielu wątków. W scenariuszach, które obejmują częste aktualizacje i stosunkowo kilka operacji odczytu, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zazwyczaj oferują one niewielkie korzyści. W scenariuszach obejmujących wiele operacji odczytu i wielu aktualizacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zwykle jest to znacznie szybsze na komputerach, które mają dowolną liczbę rdzeni.  
  
 W scenariuszach, które obejmują częste aktualizacje, można zwiększyć stopień współbieżności w, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a następnie mierzyć, aby sprawdzić, czy wydajność rośnie na komputerach, które mają więcej rdzeni. Jeśli zmienisz poziom współbieżności, unikaj operacji globalnych tak często, jak to możliwe.  
  
 W przypadku odczytywania tylko klucza lub wartości, <xref:System.Collections.Generic.Dictionary%602> jest to szybsze, ponieważ nie jest wymagana żadna synchronizacja, jeśli słownik nie jest modyfikowany przez żadne wątki.  
  
## <a name="concurrentbag"></a>Obiekt ConcurrentBag  
 W czystych scenariuszach z zakresu producentów klient <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> prawdopodobnie przestanie działać wolniej niż inne współbieżne typy kolekcji.  
  
 W mieszanych scenariuszach konsumenckich klientów <xref:System.Collections.Concurrent.ConcurrentBag%601> jest to znacznie szybsze i bardziej skalowalne niż każdy inny typ kolekcji współbieżnej dla dużych i małych obciążeń.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Gdy wymagane są semantyki ograniczania i blokowania, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> prawdopodobnie będą wykonywane szybciej niż Każda implementacja niestandardowa. Obsługuje ona również rozbudowane anulowanie, Wyliczanie i obsługę wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne dla wątków](index.md)
- [Programowanie równoległe](../../parallel-programming/index.md)
