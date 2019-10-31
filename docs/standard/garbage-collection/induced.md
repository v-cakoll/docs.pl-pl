---
title: Wywołane kolekcje
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120919"
---
# <a name="induced-collections"></a>Wywołane kolekcje
W większości przypadków moduł wyrzucania elementów bezużytecznych może określić najlepszy czas wykonywania kolekcji i należy pozwolić na jego uruchomienie niezależnie. Istnieją rzadkie sytuacje, w których wymuszona kolekcja może poprawić wydajność aplikacji. W takich przypadkach można wywołać wyrzucanie elementów bezużytecznych za pomocą metody <xref:System.GC.Collect%2A?displayProperty=nameWithType>, aby wymusić wyrzucanie elementów bezużytecznych.  
  
 Użyj metody <xref:System.GC.Collect%2A?displayProperty=nameWithType>, gdy istnieje znacząca redukcja ilości pamięci używanej w konkretnym momencie w kodzie aplikacji. Na przykład jeśli aplikacja używa złożonego okna dialogowego, które ma kilka kontrolek, wywoływanie <xref:System.GC.Collect%2A> po zamknięciu okna dialogowego może poprawić wydajność przez natychmiastowe ododzyskiwanie pamięci używanej przez okno dialogowe. Upewnij się, że aplikacja nie powoduje zbyt częstego wyrzucania elementów bezużytecznych, ponieważ może obniżyć wydajność, jeśli moduł wyrzucania elementów bezużytecznych próbuje przejąć obiekty w nieoptymalnym czasie. Możesz podać <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> wartość wyliczenia do metody <xref:System.GC.Collect%2A>, aby zbierać dane tylko wtedy, gdy zbieranie będzie produktywne, jak to opisano w następnej sekcji.  
  
## <a name="gc-collection-mode"></a>Tryb zbierania danych GC  
 Można użyć jednego z przeciążeń metody <xref:System.GC.Collect%2A?displayProperty=nameWithType>, który zawiera wartość <xref:System.GCCollectionMode>, aby określić zachowanie dla wymuszonej kolekcji w następujący sposób.  
  
|wartość `GCCollectionMode`|Opis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Używa domyślnego ustawienia wyrzucania elementów bezużytecznych dla działającej wersji platformy .NET.|  
|<xref:System.GCCollectionMode.Forced>|Wymusza natychmiastowe wyrzucanie elementów bezużytecznych. Jest to równoznaczne z wywołaniem przeciążenia <xref:System.GC.Collect?displayProperty=nameWithType>. Powoduje to pełną blokadę kolekcji wszystkich generacji.<br /><br /> Możesz również skompaktować stertę dużego obiektu, ustawiając właściwość <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> na <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> przed wymuszeniem natychmiastowego pełnego blokowania wyrzucania elementów bezużytecznych.|  
|<xref:System.GCCollectionMode.Optimized>|Umożliwia modułowi wyrzucania elementów bezużytecznych ustalenie, czy bieżący czas jest optymalny do odzyskiwania obiektów.<br /><br /> Moduł wyrzucania elementów bezużytecznych może określić, że kolekcja nie będzie wystarczająco wydajna, aby mogła być uzasadniona, w takim przypadku będzie ona zwracała bez odzyskiwania obiektów.|  
  
## <a name="background-or-blocking-collections"></a>Kolekcje w tle lub blokujące  
 Można wywołać Przeciążenie metody <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType>, aby określić, czy wywołane kolekcje są blokowane, czy nie. Typ wykonywanej kolekcji zależy od kombinacji parametrów `mode` i `blocking` metody. `mode` jest członkiem wyliczenia <xref:System.GCCollectionMode>, a `blocking` jest wartością <xref:System.Boolean>. W poniższej tabeli zestawiono interakcje `mode` i `blocking` argumentów.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> lub <xref:System.GCCollectionMode.Default>|Kolekcja blokująca jest wykonywana najszybciej, jak to możliwe. Jeśli zbieranie w tle jest w toku i generacja ma wartość 0 lub 1, Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> natychmiast wyzwala kolekcję blokującą i zwraca, gdy kolekcja zostanie zakończona. Jeśli zbieranie w tle jest w toku i parametr `generation` ma wartość 2, metoda czeka do momentu zakończenia kolekcji w tle, wyzwala kolekcję blokującą 2. generacji, a następnie zwraca wartość.|Kolekcja jest wykonywana najszybciej, jak to możliwe. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokująca. Jeśli kolekcja w tle jest już w toku, Metoda wraca natychmiast.|  
|<xref:System.GCCollectionMode.Optimized>|Może być wykonywana kolekcja blokująca, w zależności od stanu modułu wyrzucania elementów bezużytecznych i parametru `generation`. Moduł wyrzucania elementów bezużytecznych próbuje zapewnić optymalną wydajność.|Kolekcję można wykonać w zależności od stanu modułu wyrzucania elementów bezużytecznych. Metoda <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokująca. Moduł wyrzucania elementów bezużytecznych próbuje zapewnić optymalną wydajność. Jeśli kolekcja w tle jest już w toku, Metoda wraca natychmiast.|  
  
## <a name="see-also"></a>Zobacz także

- [Tryby opóźnienia](../../../docs/standard/garbage-collection/latency.md)
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
