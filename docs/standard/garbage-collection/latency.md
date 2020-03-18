---
title: Tryby opóźnienia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: a8eaf0c80aa32978eead80c51a905cbcd66a537b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283594"
---
# <a name="latency-modes"></a>Tryby opóźnienia

Aby odzyskać obiekty, moduł zbierający elementy bezużyteczne (GC) musi zatrzymać wszystkie wątki wykonujące w aplikacji. Okres, w którym moduł odśmiecania pamięci jest aktywny jest określany jako jego *opóźnienie*.

W niektórych sytuacjach, takich jak gdy aplikacja pobiera dane lub wyświetla zawartość, pełne wyrzucanie elementów bezużytecznych może wystąpić w krytycznym czasie i utrudniać wydajność. Można dostosować natrętność modułu odśmiecania <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> pamięci, ustawiając właściwość na jedną z <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> wartości.

## <a name="low-latency-settings"></a>Ustawienia małych opóźnień

Przy użyciu "niskie" ustawienie opóźnienia oznacza moduł zbierający elementy bezużyteczne wnika mniej w aplikacji. Wyrzucanie elementów bezużytecznych jest bardziej konserwatywne w kwestii odzyskiwania pamięci.

Wyliczenie <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> zawiera dwa ustawienia małych opóźnień:

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) pomija kolekcje generacji 2 i wykonuje tylko kolekcje generacji 0 i 1. Może być używany tylko przez krótki okres czasu. Przez dłuższy czas, jeśli system jest pod ciśnieniem pamięci, moduł zbierający elementy bezużyteczne wyzwoli kolekcję, która może na chwilę wstrzymać aplikację i zakłócić operację o krytycznym znaczeniu czasowym. To ustawienie jest dostępne tylko dla wyrzucania elementów bezużytecznych stacji roboczej.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) pomija kolekcje pierwszego planu generacji 2 i wykonuje tylko kolekcje generacji 0, 1 i background generation 2. Może być używany przez dłuższy czas i jest dostępny zarówno dla stacji roboczej, jak i wyrzucania elementów bezużytecznych serwera. Tego ustawienia nie można użyć, jeśli wyrzucanie elementów bezużytecznych w tle jest wyłączone.

W okresach małych opóźnień kolekcje generacji 2 są pomijane, chyba że wystąpią następujące czynności:

- System odbiera powiadomienie o małej ilości pamięci z systemu operacyjnego.

- Kod aplikacji indukuje <xref:System.GC.Collect%2A?displayProperty=nameWithType> kolekcję, wywołując metodę `generation` i określając 2 dla parametru.

## <a name="scenarios"></a>Scenariusze

W poniższej tabeli wymieniono <xref:System.Runtime.GCLatencyMode> scenariusze aplikacji służące do używania wartości:

|Tryb opóźnienia|Scenariusze aplikacji|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|Dla aplikacji, które nie mają interfejsu użytkownika (UI) lub operacji po stronie serwera.<br /><br />Gdy wyrzucanie elementów bezużytecznych w tle jest wyłączone, jest to domyślny tryb dla stacji roboczej i wyrzucania elementów bezużytecznych serwera. <xref:System.Runtime.GCLatencyMode.Batch>mode zastępuje również ustawienie [gcConcurrent,](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) czyli zapobiega kolekcjom tła lub równoczesnych.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|Dla większości aplikacji, które mają interfejsu.<br /><br />Jest to domyślny tryb dla stacji roboczej i wyrzucania elementów bezużytecznych serwera. Jednak jeśli aplikacja jest hostowana, ustawienia modułu odśmiecania pamięci procesu hostingu mają pierwszeństwo.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|W przypadku aplikacji, które mają krótkoterminowe, zależne od czasu operacje, podczas których przerwy w wyrzucaniu pamięci mogą być uciążliwe. Na przykład aplikacje, które renderują animacje lub funkcje pozyskiwania danych.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|W przypadku aplikacji, które mają operacje zależne od czasu dla zamkniętego, ale potencjalnie dłuższego czasu, w którym przerwy w wyrzucaniu pamięci mogą być uciążliwe. Na przykład aplikacje, które wymagają szybkiego czasu reakcji w miarę zmian danych rynkowych w godzinach handlu.<br /><br />Ten tryb powoduje większy rozmiar sterty zarządzanej niż inne tryby. Ponieważ nie kompaktowa sterty zarządzanej, możliwe jest wyższe fragmentacji. Upewnij się, że dostępna jest wystarczająca ilość pamięci.|

## <a name="guidelines-for-using-low-latency"></a>Wskazówki dotyczące korzystania z małych opóźnień

Korzystając z trybu [GCLatencyMode.LowLatency,](xref:System.Runtime.GCLatencyMode.LowLatency) należy wziąć pod uwagę następujące wskazówki:

- Okres czasu w małym opóźnieniu należy zachować tak krótko, jak to możliwe.

- Należy unikać przydzielania dużych ilości pamięci w okresach małych opóźnień. Powiadomienia o małej ilości pamięci mogą wystąpić, ponieważ wyrzucanie elementów bezużytecznych odzyskuje mniej obiektów.

- W trybie małych opóźnień zminimalizuj liczbę nowych alokacji, w szczególności alokacje na stercie dużych obiektów i przypiętych obiektów.

- Należy pamiętać o wątków, które mogą być przydzielanie. Ponieważ <xref:System.Runtime.GCSettings.LatencyMode%2A> ustawienie właściwości jest dla <xref:System.OutOfMemoryException> całego procesu, wyjątki mogą być generowane na dowolnym wątku, który jest przydzielanie.

- Zawijanie kodu o małym opóźnieniu w regionach ograniczonego wykonywania. Aby uzyskać więcej informacji, zobacz [Regiony ograniczonewykonanie](../../../docs/framework/performance/constrained-execution-regions.md).

- Można wymusić kolekcji generacji 2 w okresie <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> małych opóźnień, wywołując metodę.

## <a name="see-also"></a>Zobacz też

- <xref:System.GC?displayProperty=nameWithType>
- [Wywołane kolekcje](../../../docs/standard/garbage-collection/induced.md)
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
