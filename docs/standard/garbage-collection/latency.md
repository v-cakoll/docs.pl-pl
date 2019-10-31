---
title: Tryby opóźnienia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 8833c88c3221c0a375011eb62dd712340f7e89cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120908"
---
# <a name="latency-modes"></a>Tryby opóźnienia
Aby odzyskiwać obiekty, Moduł wyrzucania elementów bezużytecznych musi zatrzymać wszystkie wątki wykonywane w aplikacji. W niektórych sytuacjach, na przykład gdy aplikacja pobiera dane lub wyświetla zawartość, pełne wyrzucanie elementów bezużytecznych może wystąpić w krytycznym czasie i utrudnić wydajność. Można dostosować inwazyjność modułu wyrzucania elementów bezużytecznych, ustawiając właściwość <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> na jedną z wartości <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.  
  
 Opóźnienie odnosi się do czasu, przez który moduł zbierający elementy bezużyteczne w aplikacji. W przypadku małych okresów opóźnienia Moduł wyrzucania elementów bezużytecznych jest bardziej ostrożny i mniej inwazyjny w odzyskiwaniu obiektów. Wyliczenie <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> zapewnia dwa ustawienia małych opóźnień:  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> pomija kolekcje generacji 2 i wykonuje tylko kolekcje generacji 0 i 1. Może być używany tylko przez krótki okresy czasu. W dłuższym czasie, jeśli system jest w obszarze pamięci, Moduł wyrzucania elementów bezużytecznych wywoła kolekcję, która może krótko zawieszać aplikację i przerwać operację krytyczną czasu. To ustawienie jest dostępne tylko dla wyrzucania elementów bezużytecznych stacji roboczej.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> pomija kolekcje generacji pierwszego planu 2 i wykonuje tylko kolekcje generacji 0, 1 i 2. generacji w tle. Może być używany przez dłuższy okres czasu i jest dostępny zarówno dla stacji roboczej, jak i serwera. Nie można użyć tego ustawienia, jeśli [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączone.  
  
 Podczas małych okresów opóźnienia kolekcje 2 generacji są pomijane, chyba że wystąpią następujące sytuacje:  
  
- System odbiera powiadomienie o niskim poziomie pamięci z systemu operacyjnego.  
  
- Kod aplikacji wywołuje kolekcję przez wywołanie metody <xref:System.GC.Collect%2A?displayProperty=nameWithType> i określenie 2 dla parametru `generation`.  
  
 W poniższej tabeli wymieniono scenariusze aplikacji dotyczące używania wartości <xref:System.Runtime.GCLatencyMode>.  
  
|Tryb opóźnień|Scenariusze aplikacji|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|W przypadku aplikacji, które nie mają interfejsu użytkownika ani operacji po stronie serwera.<br /><br /> Jest to domyślny tryb, gdy [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączone.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Dla większości aplikacji, które mają interfejs użytkownika.<br /><br /> Jest to domyślny tryb, gdy włączone jest [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) .|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|W przypadku aplikacji, które mają krótkoterminowe, zależne od czasu operacje, w których przerwy między modułem wyrzucania elementów bezużytecznych mogą powodować zakłócenia. Na przykład aplikacje, które wykonują renderowanie animacji lub funkcje pozyskiwania danych.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|W przypadku aplikacji, które mają dane zależne od czasu, ale dłuższy czas, w którym przerwy z modułu wyrzucania elementów bezużytecznych mogą być zakłócone. Na przykład aplikacje, które wymagają krótkich czasów odpowiedzi jako zmiany danych rynkowych w godzinach pracy.<br /><br /> Ten tryb powoduje zwiększenie rozmiaru zarządzanego sterty niż inne tryby. Ponieważ nie kompaktuje sterty zarządzanej, możliwe jest zwiększenie fragmentacji. Upewnij się, że dostępna jest wystarczająca ilość pamięci.|  
  
## <a name="guidelines-for-using-low-latency"></a>Wskazówki dotyczące korzystania z małych opóźnień  
 W przypadku korzystania z trybu <xref:System.Runtime.GCLatencyMode.LowLatency> należy wziąć pod uwagę następujące wytyczne:  
  
- Przechowuj okres czasu w małych opóźnieniach, tak jak to możliwe.  
  
- Unikaj alokowania dużych ilości pamięci podczas okresów o małym opóźnieniu. Powiadomienia o niskiej ilości pamięci mogą wystąpić, ponieważ odzyskiwanie pamięci przejmuje mniej obiektów.  
  
- W trybie niskiego opóźnienia Minimalizuj liczbę dokonanych przydziałów, w szczególności przydziały do sterty dużego obiektu i przypiętych obiektów.  
  
- Należy pamiętać o wątkach, które mogą być przydzielane. Ponieważ ustawienie właściwości <xref:System.Runtime.GCSettings.LatencyMode%2A> to cały proces, można wygenerować <xref:System.OutOfMemoryException> na dowolnym wątku, który może przydzielić.  
  
- Zawijaj kod małych opóźnień w regionach ograniczonego wykonywania (Aby uzyskać więcej informacji, zobacz [ograniczone regiony wykonywania](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- Można wymusić zbieranie 2 kolekcji w okresie o małym opóźnieniu, wywołując metodę <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.GC?displayProperty=nameWithType>
- [Wywołane kolekcje](../../../docs/standard/garbage-collection/induced.md)
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
