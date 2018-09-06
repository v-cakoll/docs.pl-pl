---
title: Tryby opóźnienia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3440e0869bfd131f8a57a74af6105716d4b72935
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883725"
---
# <a name="latency-modes"></a>Tryby opóźnienia
Do odzyskania obiektów, wyrzucanie elementów bezużytecznych należy zatrzymać wszystkie wątki wykonywania w aplikacji. W niektórych sytuacjach, np. gdy aplikacja pobiera dane lub wyświetla zawartość pełne wyrzucanie elementów bezużytecznych występuje w czasie krytycznych i utrudniać wydajności. Można dostosować wszechobecność moduł zbierający elementy bezużyteczne, ustawiając <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> jedną z właściwości <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> wartości.  
  
 Opóźnienie odnosi się do czasu, który narusza moduł odśmiecania pamięci, w aplikacji. W okresach, małe opóźnienia moduł odśmiecania pamięci jest bardziej konserwatywnego i płynniejsza w odzyskiwaniu obiektów. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Wyliczenia zawiera dwa ustawienia małe opóźnienia:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency> Pomija kolekcji generacji 2, a następnie wykonuje tylko kolekcji generacji 0 i 1. Może służyć tylko w przypadku krótkich okresach czasu. Przez dłuższy czas Jeśli system jest w dużym wykorzystaniu pamięci, moduł zbierający elementy bezużyteczne wyzwoli kolekcji, co może chwilę Zatrzymywanie aplikacji i zakłócić wrażliwego na czas operacji. To ustawienie jest dostępne tylko dla stacji roboczej wyrzucania elementów bezużytecznych.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> Pomija kolekcje geenracji 2 pierwszego planu i wykonuje tylko generacji 0, 1 i kolekcje geenracji 2 w tle. Może służyć przez dłuższy czas i jest dostępna dla wyrzucania elementów bezużytecznych stacji roboczej i serwerze. Nie można użyć tego ustawienia, jeśli [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączona.  
  
 W okresach, małe opóźnienia kolekcji generacji 2 są pomijane, chyba że mają miejsce następujące zdarzenia:  
  
-   System otrzyma powiadomienie o małej ilości pamięci systemu operacyjnego.  
  
-   Kod aplikacji wywołuje kolekcji przez wywołanie metody <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody i określając 2- `generation` parametru.  
  
 Poniższa tabela zawiera listę scenariuszy aplikacji, aby uzyskać przy użyciu <xref:System.Runtime.GCLatencyMode> wartości.  
  
|Tryb opóźnienia|Scenariusze aplikacji|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|W przypadku aplikacji, które mają nie interfejsu użytkownika lub operacji po stronie serwera.<br /><br /> Jest to domyślny tryb podczas [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączona.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|W przypadku większości aplikacji, które mają interfejs użytkownika.<br /><br /> Jest to domyślny tryb podczas [współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest włączona.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|W przypadku aplikacji, które mają krótkoterminowej operacje zależne od czasu, podczas których przerw w pracy z modułu odśmiecania pamięci może być szkodliwe. Na przykład aplikacje, które czy renderowania lub dane funkcji przejęcia animacji.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Dla aplikacji, które są zależne od czasu zawarte, ale potencjalnie dłuższy czas trwania czas, w którym przerw w pracy z modułu odśmiecania pamięci może być szkodliwe. Na przykład aplikacji, które wymagają szybkie czasy związku ze zmianą danych rynkowych poza godzinami handlowych.<br /><br /> W tym trybie powoduje zwiększenie rozmiaru sterty zarządzanej, niż inne tryby. Ponieważ nie to kompaktowania sterty zarządzanej, wyższe fragmentacji jest możliwe. Upewnij się, że jest dostępna wystarczająca ilość pamięci.|  
  
## <a name="guidelines-for-using-low-latency"></a>Wytyczne dotyczące korzystania z małymi opóźnieniami  
 Kiedy używasz <xref:System.Runtime.GCLatencyMode.LowLatency> trybie, należy wziąć pod uwagę następujące wytyczne:  
  
-   Zachowaj czas w możliwie krótkie małymi opóźnieniami.  
  
-   Należy unikać przydzielanie wysokiej ilości pamięci w okresach małymi opóźnieniami. Powiadomienia o małej ilości pamięci może być fakt, że wyrzucanie elementów bezużytecznych odzyskuje mniejszą liczbę obiektów.  
  
-   W trybie małych opóźnień, zminimalizować liczbę alokacji wprowadzanych w określonej alokacji na sterty obiektów wielkich i przypiętych obiektów.  
  
-   Należy pamiętać o wątki, które można przydzielania. Ponieważ <xref:System.Runtime.GCSettings.LatencyMode%2A> ustawienie właściwości jest całego procesu, można wygenerować <xref:System.OutOfMemoryException> dotyczące dowolnego wątku, który może być przydzielania.  
  
-   Zawijania kodu niskie opóźnienia w ograniczone regiony wykonania (Aby uzyskać więcej informacji, zobacz [ograniczone regiony wykonania](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   Można wymusić kolekcje geenracji 2 okresie małych opóźnień, wywołując <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.GC?displayProperty=nameWithType>  
- [Wywołane kolekcje](../../../docs/standard/garbage-collection/induced.md)  
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
