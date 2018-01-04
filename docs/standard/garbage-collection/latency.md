---
title: "Tryby opóźnienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d0ac0db376ad7cd4aa139ed0eb065a5ba33836c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="latency-modes"></a>Tryby opóźnienia
Aby odzyskać obiektów, moduł zbierający elementy bezużyteczne należy zatrzymać wszystkie wątki wykonywane w aplikacji. W niektórych sytuacjach, na przykład w przypadku aplikacji pobiera dane lub wyświetla zawartość pełnego wyrzucania elementów bezużytecznych mogą wystąpić jednocześnie krytyczne i utrudniać wydajności. Przez ustawienie można dostosować intrusiveness modułu zbierającego elementy bezużyteczne <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> jedną z właściwości <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> wartości.  
  
 Czas oczekiwania odwołuje się do czasu, który narusza modułu zbierającego elementy bezużyteczne w aplikacji. W okresach, małe opóźnienia moduł zbierający elementy bezużyteczne jest bardziej zachowawcze i ta opcja jest mniej pożądana w odzyskiwanie obiektów. <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> Wyliczenie zawiera dwa ustawienia małe opóźnienia:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency>Pomija generacji 2, a następnie wykonuje tylko kolekcje generacji 0 i 1. Może służyć tylko w krótkich okresach czasu. Przez dłuższy czas system występuje duże wykorzystanie pamięci, moduł zbierający elementy bezużyteczne wyzwoli kolekcji krótko można wstrzymać aplikacji i zakłócić wrażliwego na czas operacji. To ustawienie jest dostępne tylko w przypadku stacji roboczej wyrzucanie elementów bezużytecznych.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency>Pomija kolekcje generacji 2 pierwszego planu i przeprowadza tylko generacji 0, 1 i kolekcje generacji 2 tła. Może służyć do dłuższy czas i jest dostępny dla zarówno stacji roboczej i serwerze wyrzucanie elementów bezużytecznych. Nie można użyć tego ustawienia, jeśli [współbieżne odzyskiwanie pamięci](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączona.  
  
 W okresach, małe opóźnienia kolekcje generacji 2 są pomijane, chyba że są następujące operacje:  
  
-   System otrzyma powiadomienie o małej ilości pamięci systemu operacyjnego.  
  
-   Kod aplikacji wywołuje kolekcji, wywołując <xref:System.GC.Collect%2A?displayProperty=nameWithType> — metoda i określając 2 dla `generation` parametru.  
  
 W poniższej tabeli wymieniono scenariusze aplikacji przy użyciu <xref:System.Runtime.GCLatencyMode> wartości.  
  
|Tryb opóźnienia|Scenariusze aplikacji|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Dla aplikacji, które nie zawierają interfejsu użytkownika ani operacji po stronie serwera.<br /><br /> Jest to domyślny tryb podczas [współbieżne odzyskiwanie pamięci](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest wyłączona.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Dla większości aplikacji, które mają interfejsu użytkownika.<br /><br /> Jest to domyślny tryb podczas [współbieżne odzyskiwanie pamięci](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) jest włączona.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Dla aplikacji, które mają operacji krótkoterminowej, zależne od czasu, w których może stanowić zakłócenie przerw w działaniu z modułu zbierającego elementy bezużyteczne. Na przykład aplikacje, które czy renderowania lub dane funkcji nabycia animacji.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Dla aplikacji, które mają harmonogramów działań zawartych w niej jednak potencjalnie dłuższy okres czasu, w którym może stanowić zakłócenie przerw w działaniu z modułu zbierającego elementy bezużyteczne. Na przykład aplikacje wymagające szybkich odpowiedzi razy zmiany danych z rynku handlowym godzinach.<br /><br /> W tym trybie powoduje zwiększenie rozmiaru sterty zarządzanej niż innych trybów. Ponieważ go nie skompaktować sterty zarządzanej, możliwe jest wyższy fragmentacji. Upewnij się, że jest dostępna wystarczająca ilość pamięci.|  
  
## <a name="guidelines-for-using-low-latency"></a>Wskazówki dotyczące używania małe opóźnienia  
 Jeśli używasz <xref:System.Runtime.GCLatencyMode.LowLatency> trybie, należy wziąć pod uwagę następujące wytyczne:  
  
-   Należy małych opóźnieniach możliwie krótki okres.  
  
-   Unikać wysokiej ilości pamięci w okresach, małe opóźnienia. Powiadomienia o małej ilości pamięci może być spowodowany pamięci zwraca mniejszą liczbę obiektów.  
  
-   W trybie małych opóźnieniach zminimalizować liczbę alokacji przez użytkownika, w szczególności alokacje na sterty dużych obiektów, a następnie unieruchomionych obiektów znajdujących się.  
  
-   Należy pamiętać o wątków, które można alokacji. Ponieważ <xref:System.Runtime.GCSettings.LatencyMode%2A> ustawienie właściwości jest całego procesu, można wygenerować <xref:System.OutOfMemoryException> w którymkolwiek wątku, który może być alokacji.  
  
-   Zawijanie kodu małe opóźnienia w ograniczone regiony wykonania (Aby uzyskać więcej informacji, zobacz [ograniczone regiony wykonania](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   Kolekcje generacji 2 można wymusić okresie małe opóźnienia przez wywołanie metody <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.GC?displayProperty=nameWithType>  
 [Wywołane kolekcje](../../../docs/standard/garbage-collection/induced.md)  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
