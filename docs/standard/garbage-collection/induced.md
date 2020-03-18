---
title: Wywołane kolekcje
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120919"
---
# <a name="induced-collections"></a>Wywołane kolekcje
W większości przypadków moduł zbierający elementy bezużyteczne można określić najlepszy czas, aby wykonać kolekcję i należy pozwolić jej uruchomić niezależnie. Istnieją rzadkie sytuacje, gdy wymuszona kolekcja może poprawić wydajność aplikacji. W takich przypadkach można wywołać wyrzucania <xref:System.GC.Collect%2A?displayProperty=nameWithType> elementów bezużytecznych przy użyciu metody wymusić wyrzucania elementów bezużytecznych.  
  
 Użyj <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody, gdy występuje znaczne zmniejszenie ilości pamięci używanej w określonym punkcie w kodzie aplikacji. Na przykład jeśli aplikacja używa złożonego okna dialogowego, które ma kilka formantów, wywołanie <xref:System.GC.Collect%2A> po zamknięciu okna dialogowego może zwiększyć wydajność, natychmiast odzyskując pamięć używaną przez okno dialogowe. Upewnij się, że aplikacja nie jest wywoływanie wyrzucania elementów bezużytecznych zbyt często, ponieważ może to zmniejszyć wydajność, jeśli moduł zbierający elementy bezużyteczne próbuje odzyskać obiekty w nieoptymalnych czasach. Można podać <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> wartość wyliczenia <xref:System.GC.Collect%2A> do metody do zbierania tylko wtedy, gdy kolekcja będzie produktywne, zgodnie z omówieniem w następnej sekcji.  
  
## <a name="gc-collection-mode"></a>Tryb zbierania GC  
 Można użyć jednego <xref:System.GC.Collect%2A?displayProperty=nameWithType> z przeciążeń <xref:System.GCCollectionMode> metody, która zawiera wartość, aby określić zachowanie dla kolekcji wymuszone w następujący sposób.  
  
|`GCCollectionMode`Wartość|Opis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Używa domyślnego ustawienia wyrzucania elementów bezużytecznych dla uruchomionej wersji programu .NET.|  
|<xref:System.GCCollectionMode.Forced>|Wymusza wyrzucanie elementów bezużytecznych natychmiast. Jest to równoważne <xref:System.GC.Collect?displayProperty=nameWithType> wywołanie przeciążenia. Skutkuje to pełnym blokowaniem kolekcji wszystkich pokoleń.<br /><br /> Można również skompaktować sterty <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> dużych <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> obiektów, ustawiając właściwość przed wymuszeniem natychmiastowego pełnego blokowania wyrzucania elementów bezużytecznych.|  
|<xref:System.GCCollectionMode.Optimized>|Umożliwia modułowi odśmiecania pamięci, aby ustalić, czy bieżący czas jest optymalny do odzyskania obiektów.<br /><br /> Moduł zbierający elementy bezużyteczne może określić, że kolekcja nie będzie wystarczająco produktywne, aby być uzasadnione, w którym to przypadku zostanie zwrócony bez odzyskiwania obiektów.|  
  
## <a name="background-or-blocking-collections"></a>Kolekcja tła lub blokowania  
 Można wywołać <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> przeciążenie metody, aby określić, czy indukowana kolekcja blokuje, czy nie. Typ wykonywanej kolekcji zależy od kombinacji metody `mode` `blocking` i parametrów. `mode`jest członkiem wyliczenia <xref:System.GCCollectionMode> i `blocking` jest <xref:System.Boolean> wartością. W poniższej tabeli podsumowano `mode` `blocking` interakcję argumentów i argumentów.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> lub <xref:System.GCCollectionMode.Default>|Kolekcja blokująca jest wykonywana tak szybko, jak to możliwe. Jeśli kolekcja w tle jest w toku i <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> generacji jest 0 lub 1, metoda natychmiast wyzwala blokowania kolekcji i zwraca po zakończeniu kolekcji. Jeśli kolekcja w tle jest `generation` w toku, a parametr jest 2, metoda czeka, aż kolekcja w tle jest gotowy, wyzwala blokowanie generacji 2 kolekcji, a następnie zwraca.|Kolekcja jest wykonywana tak szybko, jak to możliwe. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal można wykonać zbieranie blokujące. Jeśli kolekcja w tle jest już w toku, metoda zwraca natychmiast.|  
|<xref:System.GCCollectionMode.Optimized>|Zbieranie blokowania mogą być wykonywane, w zależności od stanu modułu odśmiecania pamięci i parametru. `generation` Moduł zbierający elementy bezużyteczne próbuje zapewnić optymalną wydajność.|Kolekcja może być wykonywane, w zależności od stanu modułu odśmiecania pamięci. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal można wykonać zbieranie blokujące. Moduł zbierający elementy bezużyteczne próbuje zapewnić optymalną wydajność. Jeśli kolekcja w tle jest już w toku, metoda zwraca natychmiast.|  
  
## <a name="see-also"></a>Zobacz też

- [Tryby opóźnienia](../../../docs/standard/garbage-collection/latency.md)
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
