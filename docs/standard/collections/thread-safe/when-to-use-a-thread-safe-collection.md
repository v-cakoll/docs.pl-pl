---
title: Kiedy należy używać kolekcji bezpiecznych wątkowo
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711223"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kiedy należy używać kolekcji bezpiecznych wątkowo
.NET Framework 4 wprowadza pięć nowych typów kolekcji, które są specjalnie zaprojektowane do obsługi operacji dodawania i usuwania wielowątkowych. Aby osiągnąć bezpieczeństwo wątków, te nowe typy używają różnego rodzaju wydajnych mechanizmów blokowania i synchronizacji bez blokady. Synchronizacja dodaje obciążenie do operacji. Ilość obciążenie zależy od rodzaju synchronizacji, który jest używany, rodzaj operacji, które są wykonywane i inne czynniki, takie jak liczba wątków, które próbują jednocześnie uzyskać dostęp do kolekcji.  
  
 W niektórych scenariuszach obciążenie synchronizacji jest znikome i umożliwia typ wielowątkowy do wykonywania znacznie szybciej i skalować znacznie lepiej niż jego odpowiednik nie-wątku bezpieczne, gdy chronione przez blokadę zewnętrzną. W innych scenariuszach obciążenie może spowodować typu bezpiecznego dla wątków do wykonywania i skalowania o tym samym lub nawet wolniej niż zewnętrznie zablokowane, niewątkowo-bezpieczne wersji tego typu.  
  
 W poniższych sekcjach przedstawiono ogólne wskazówki dotyczące używania kolekcji bezpiecznej dla wątków w porównaniu z jego odpowiednikiem niebezpiecznym od wątków, który ma blokadę dostarczoną przez użytkownika wokół operacji odczytu i zapisu. Ponieważ wydajność może się różnić w zależności od wielu czynników, wskazówki nie są specyficzne i niekoniecznie są ważne we wszystkich okolicznościach. Jeśli wydajność jest bardzo ważna, najlepszym sposobem określenia typu kolekcji jest pomiar wydajności na podstawie reprezentatywnych konfiguracji i obciążeń komputera. W tym dokumencie użyto następujących terminów:  
  
 *Czysty scenariusz producent-konsument*  
 Każdy dany wątek jest dodawanie lub usuwanie elementów, ale nie oba.  
  
 *Mieszany scenariusz producent-konsument*  
 Każdy dany wątek jest zarówno dodawanie i usuwanie elementów.  
  
 *Przyspieszenie*  
 Szybsza wydajność algorytmiczna w stosunku do innego typu w tym samym scenariuszu.  
  
 *Skalowalność*  
 Wzrost wydajności, który jest proporcjonalny do liczby rdzeni na komputerze. Algorytm, który skaluje się szybciej na ośmiu rdzeniach niż na dwóch rdzeniach.  
  
## <a name="concurrentqueuet-vs-queuet"></a>Kolejka współbieżna(T) a kolejka (T)  
 W scenariuszach czystego producenta-konsumenta, gdzie czas przetwarzania dla każdego elementu <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> jest bardzo mały <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> (kilka instrukcji), a następnie może zaoferować skromne korzyści wydajności w przypadku blokady zewnętrznej. W tym <xref:System.Collections.Concurrent.ConcurrentQueue%601> scenariuszu działa najlepiej, gdy jeden dedykowany wątek jest w kolejce i jeden dedykowany wątek jest de-kolejki. Jeśli ta reguła nie <xref:System.Collections.Generic.Queue%601> zostanie wymuszona, może nawet działać nieco szybciej niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> na komputerach, które mają wiele rdzeni.  
  
 Gdy czas przetwarzania wynosi około 500 FLOPS (operacje zmiennoprzecinkowe) lub więcej, to reguła dwuwątkowa nie ma zastosowania do <xref:System.Collections.Concurrent.ConcurrentQueue%601>, który następnie ma bardzo dobrą skalowalność. <xref:System.Collections.Generic.Queue%601>nie skalują się dobrze w tym scenariuszu.  
  
 W mieszanych scenariuszach producent-konsument, gdy czas <xref:System.Collections.Generic.Queue%601> przetwarzania jest bardzo mały, <xref:System.Collections.Concurrent.ConcurrentQueue%601> a, który ma zewnętrzną skalę blokady lepiej niż ma. Jednak gdy czas przetwarzania wynosi około 500 <xref:System.Collections.Concurrent.ConcurrentQueue%601> FLOPÓW lub więcej, waga jest lepsza.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack kontra Stos  
 W scenariuszach czystego producenta-konsumenta, gdy czas <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> przetwarzania jest bardzo mały, a następnie i że ma blokadę zewnętrzną prawdopodobnie będzie wykonywać mniej więcej tyle samo z jednym dedykowanym wątku pchania i jeden dedykowany wątek popping. Jednak wraz ze wzrostem liczby wątków oba typy spowalniają z <xref:System.Collections.Generic.Stack%601> powodu zwiększonej <xref:System.Collections.Concurrent.ConcurrentStack%601>rywalizacji i mogą działać lepiej niż . Gdy czas przetwarzania wynosi około 500 FLOPÓw lub więcej, oba typy są skalowane z szybkością o tej samej szybkości.  
  
 W mieszanych scenariuszach <xref:System.Collections.Concurrent.ConcurrentStack%601> producent-konsument jest szybszy zarówno dla małych, jak i dużych obciążeń.  
  
 Korzystanie z <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> i <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> może znacznie przyspieszyć czas dostępu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Słownik  
 Ogólnie rzecz biorąc <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> należy użyć w każdym scenariuszu, w którym są dodawanie i aktualizowanie kluczy lub wartości jednocześnie z wielu wątków. W scenariuszach, które obejmują częste aktualizacje i stosunkowo niewiele odczytów, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zazwyczaj oferuje skromne korzyści. W scenariuszach, które obejmują wiele <xref:System.Collections.Concurrent.ConcurrentDictionary%602> odczytów i wiele aktualizacji, zazwyczaj jest znacznie szybciej na komputerach, które mają dowolną liczbę rdzeni.  
  
 W scenariuszach, które obejmują częste aktualizacje, można <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zwiększyć stopień współbieżności w, a następnie zmierzyć, aby zobaczyć, czy zwiększa wydajność na komputerach, które mają więcej rdzeni. Jeśli zmienisz poziom współbieżności, należy unikać operacji globalnych, jak to możliwe.  
  
 Jeśli czytasz tylko klucz <xref:System.Collections.Generic.Dictionary%602> lub wartości, jest szybsze, ponieważ synchronizacja nie jest wymagana, jeśli słownik nie jest modyfikowany przez żadne wątki.  
  
## <a name="concurrentbag"></a>Concurrentbag  
 W scenariuszach czystego producenta-konsumenta, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> prawdopodobnie będzie działać wolniej niż inne typy kolekcji równoczesnych.  
  
 W mieszanych scenariuszach <xref:System.Collections.Concurrent.ConcurrentBag%601> producent-konsument jest zazwyczaj znacznie szybszy i bardziej skalowalny niż jakikolwiek inny typ kolekcji jednocześnie dla dużych i małych obciążeń.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Gdy wymagane są ograniczające i blokujące <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> semantyki, prawdopodobnie będzie działać szybciej niż implementacja niestandardowa. Obsługuje również rozbudowane anulowanie, wyliczenie i obsługę wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
