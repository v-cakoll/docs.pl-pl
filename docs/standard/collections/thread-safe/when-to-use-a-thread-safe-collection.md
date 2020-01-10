---
title: Kiedy należy używać kolekcji bezpiecznych wątkowo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711223"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kiedy należy używać kolekcji bezpiecznych wątkowo
W .NET Framework 4 wprowadzono pięć nowych typów kolekcji, które są specjalnie przeznaczone do obsługi operacji dodawania i usuwania wielowątkowych wątków. Aby zapewnić bezpieczeństwo wątków, te nowe typy wykorzystują różne rodzaje wydajnych mechanizmów synchronizacji i blokowania bez blokady. Synchronizacja dodaje narzuty do operacji. Ilość narzutów zależy od rodzaju używanej synchronizacji, rodzaju wykonywanych operacji oraz innych czynników, takich jak liczba wątków, które próbują jednocześnie uzyskać dostęp do kolekcji.  
  
 W niektórych scenariuszach narzuty związane z synchronizacją są nieznaczne i umożliwiają znacznie szybszy i bardziej skalowalne skalowanie, w porównaniu z niebezpiecznym wątkem, w przypadku ochrony przez zewnętrzną blokadę. W innych scenariuszach narzuty mogą spowodować, że typ bezpieczny wątkowo będzie wykonywany i skalowalny na tym samym lub nawet wolniej niż zablokowana zewnętrznie, niezabezpieczona przed wątkiem wersja typu.  
  
 W poniższych sekcjach znajdują się ogólne wskazówki dotyczące sytuacji, w których należy używać kolekcji bezpiecznej dla wątków, a jej bezwzględnie niebezpieczny wątek, która ma blokadę dostarczoną przez użytkownika wokół operacji odczytu i zapisu. Ze względu na to, że wydajność może się różnić w zależności od wielu czynników, wskazówki nie są specyficzne i nie zawsze są ważne we wszystkich okolicznościach. Jeśli wydajność jest bardzo ważna, najlepszym sposobem określenia typu kolekcji, który ma być używany, jest pomiar wydajności na podstawie konfiguracji i obciążeń na reprezentatywnym komputerze. W tym dokumencie są stosowane następujące warunki:  
  
 *Czysty scenariusz dla producentów*  
 Każdy dany wątek dodaje lub usuwa elementy, ale nie oba.  
  
 *Mieszany scenariusz dla klientów*  
 Każdy dany wątek jednocześnie dodaje i usuwa elementy.  
  
 *Przyspieszenie*  
 Szybsza wydajność algorytmu względem innego typu w tym samym scenariuszu.  
  
 *Skalowalność*  
 Zwiększenie wydajności, która jest proporcjonalna do liczby rdzeni na komputerze. Algorytm, który skaluje się szybciej na osiem rdzeni niż w przypadku dwóch rdzeni.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue (T) a kolejka (T)  
 W czystych scenariuszach dla producentów, w których czas przetwarzania dla każdego elementu jest bardzo mały (kilka instrukcji), <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> może oferować niewielkie korzyści z wydajności na <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, które mają zewnętrzną blokadę. W tym scenariuszu <xref:System.Collections.Concurrent.ConcurrentQueue%601> wykonuje się najlepiej, gdy jeden dedykowany wątek jest kolejką, a jeden dedykowany wątek zostaje cofnięty. Jeśli ta reguła nie jest wymuszana, <xref:System.Collections.Generic.Queue%601> może nawet działać nieco szybciej niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> na komputerach z wieloma rdzeniami.  
  
 Gdy czas przetwarzania wynosi około 500 FLOPS (operacji zmiennoprzecinkowych) lub więcej, reguła dwuwątkowa nie ma zastosowania do <xref:System.Collections.Concurrent.ConcurrentQueue%601>, który następnie ma bardzo dobrą skalowalność. w tym scenariuszu <xref:System.Collections.Generic.Queue%601> nie skaluje się prawidłowo.  
  
 W mieszanych scenariuszach konsumenckich klientów, gdy czas przetwarzania jest bardzo mały, <xref:System.Collections.Generic.Queue%601>, który ma skalę zewnętrzną, jest skalowalny przez <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Jeśli jednak czas przetwarzania wynosi około 500 FLOPS lub więcej, <xref:System.Collections.Concurrent.ConcurrentQueue%601> skaluje się lepiej.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack a stos  
 W czystych scenariuszach z zakresu producentów, gdy czas przetwarzania jest bardzo mały, <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>, które mają zewnętrzną blokadę, prawdopodobnie przestaną się tak samo w przypadku jednego dedykowanego wątku wypychania i jednego dedykowanego wątku usuwanie. Jednak w miarę wzrostu liczby wątków oba typy spowalniają działanie ze względu na zwiększoną rywalizację, a <xref:System.Collections.Generic.Stack%601> mogą działać lepiej niż <xref:System.Collections.Concurrent.ConcurrentStack%601>. Gdy czas przetwarzania ma około 500 FLOPS lub więcej, wówczas oba typy skalują o tej samej stawce.  
  
 W mieszanych scenariuszach konsumenckich klientów <xref:System.Collections.Concurrent.ConcurrentStack%601> jest szybsza dla małych i dużych obciążeń.  
  
 Użycie <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> i <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> może znacznie przyspieszyć czas dostępu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary a słownik  
 Ogólnie rzecz biorąc, użyj <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> w dowolnym scenariuszu, w którym są dodawane i aktualizowane klucze lub wartości jednocześnie z wielu wątków. W scenariuszach, które obejmują częste aktualizacje i stosunkowo kilka operacji odczytu, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zwykle oferuje niewielkie korzyści. W scenariuszach obejmujących wiele operacji odczytu i wielu aktualizacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są zwykle znacznie szybsze na komputerach, które mają dowolną liczbę rdzeni.  
  
 W scenariuszach, które obejmują częste aktualizacje, można zwiększyć stopień współbieżności w <xref:System.Collections.Concurrent.ConcurrentDictionary%602> a następnie mierzyć, aby sprawdzić, czy wydajność rośnie na komputerach, które mają więcej rdzeni. Jeśli zmienisz poziom współbieżności, unikaj operacji globalnych tak często, jak to możliwe.  
  
 W przypadku odczytywania tylko klucza lub wartości <xref:System.Collections.Generic.Dictionary%602> jest szybsze, ponieważ nie jest wymagana żadna synchronizacja, jeśli słownik nie jest modyfikowany przez żadne wątki.  
  
## <a name="concurrentbag"></a>Obiekt ConcurrentBag  
 W czystych scenariuszach z zakresu producentów, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> prawdopodobnie będą wykonywane wolniej niż inne współbieżne typy kolekcji.  
  
 W mieszanych scenariuszach konsumenckich klientów <xref:System.Collections.Concurrent.ConcurrentBag%601> jest zwykle znacznie szybsze i bardziej skalowalne niż każdy inny typ kolekcji współbieżnej dla dużych i małych obciążeń.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Gdy wymagana jest semantyka ograniczania i blokowania, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> będzie prawdopodobnie szybsza niż jakakolwiek implementacja niestandardowa. Obsługuje ona również rozbudowane anulowanie, Wyliczanie i obsługę wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
