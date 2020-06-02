---
title: Wywołane kolekcje
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 36dff45587c6c28ba17fd7389dc3863893ff8f61
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286044"
---
# <a name="induced-collections"></a>Wywołane kolekcje
W większości przypadków moduł wyrzucania elementów bezużytecznych może określić najlepszy czas wykonywania kolekcji i należy pozwolić na jego uruchomienie niezależnie. Istnieją rzadkie sytuacje, w których wymuszona kolekcja może poprawić wydajność aplikacji. W takich przypadkach można wywołać wyrzucanie elementów bezużytecznych za pomocą <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody w celu wymuszenia wyrzucania elementów bezużytecznych.  
  
 Użyj <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody, gdy istnieje znacząca redukcja ilości pamięci używanej w konkretnym momencie w kodzie aplikacji. Na przykład jeśli aplikacja używa złożonego okna dialogowego, które ma kilka kontrolek, wywoływanie, <xref:System.GC.Collect%2A> gdy okno dialogowe jest zamknięte, może poprawić wydajność przez natychmiastowe ododzyskiwanie pamięci używanej przez okno dialogowe. Upewnij się, że aplikacja nie powoduje zbyt częstego wyrzucania elementów bezużytecznych, ponieważ może obniżyć wydajność, jeśli moduł wyrzucania elementów bezużytecznych próbuje przejąć obiekty w nieoptymalnym czasie. Możesz podać <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> wartość wyliczenia do <xref:System.GC.Collect%2A> metody, która ma być zbierana tylko wtedy, gdy kolekcja będzie produktywna, jak to opisano w następnej sekcji.  
  
## <a name="gc-collection-mode"></a>Tryb zbierania danych GC  
 Można użyć jednego z <xref:System.GC.Collect%2A?displayProperty=nameWithType> przeciążeń metody, które zawiera <xref:System.GCCollectionMode> wartość, aby określić zachowanie dla wymuszonej kolekcji w następujący sposób.  
  
|`GCCollectionMode`wartościami|Opis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Używa domyślnego ustawienia wyrzucania elementów bezużytecznych dla działającej wersji platformy .NET.|  
|<xref:System.GCCollectionMode.Forced>|Wymusza natychmiastowe wyrzucanie elementów bezużytecznych. Jest to równoznaczne z wywołaniem <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenia. Powoduje to pełną blokadę kolekcji wszystkich generacji.<br /><br /> Możesz również skompaktować stertę dużego obiektu przez ustawienie <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości na <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> przed wymuszeniem natychmiastowego pełnego blokowania wyrzucania elementów bezużytecznych.|  
|<xref:System.GCCollectionMode.Optimized>|Umożliwia modułowi wyrzucania elementów bezużytecznych ustalenie, czy bieżący czas jest optymalny do odzyskiwania obiektów.<br /><br /> Moduł wyrzucania elementów bezużytecznych może określić, że kolekcja nie będzie wystarczająco wydajna, aby mogła być uzasadniona, w takim przypadku będzie ona zwracała bez odzyskiwania obiektów.|  
  
## <a name="background-or-blocking-collections"></a>Kolekcje w tle lub blokujące  
 Można wywołać <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> Przeciążenie metody, aby określić, czy wywołane kolekcje są blokowane, czy nie. Typ wykonywanej kolekcji zależy od kombinacji metody `mode` i `blocking` parametrów. `mode`jest elementem członkowskim <xref:System.GCCollectionMode> wyliczenia i `blocking` jest <xref:System.Boolean> wartością. Poniższa tabela zawiera podsumowanie interakcji z `mode` `blocking` argumentami i.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> lub <xref:System.GCCollectionMode.Default>|Kolekcja blokująca jest wykonywana najszybciej, jak to możliwe. Jeśli zbieranie w tle jest w toku, a generacja ma wartość 0 lub 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda natychmiast wyzwala kolekcję blokującą i zwraca, gdy kolekcja zostanie zakończona. Jeśli zbieranie w tle jest w toku, a `generation` parametr ma wartość 2, metoda czeka do momentu zakończenia kolekcji w tle, wyzwala kolekcję blokującą 2. generacji, a następnie zwraca wartość.|Kolekcja jest wykonywana najszybciej, jak to możliwe. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Metoda żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokująca. Jeśli kolekcja w tle jest już w toku, Metoda wraca natychmiast.|  
|<xref:System.GCCollectionMode.Optimized>|Może być wykonywana kolekcja blokująca, w zależności od stanu modułu wyrzucania elementów bezużytecznych i `generation` parametru. Moduł wyrzucania elementów bezużytecznych próbuje zapewnić optymalną wydajność.|Kolekcję można wykonać w zależności od stanu modułu wyrzucania elementów bezużytecznych. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Metoda żąda kolekcji w tle, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokująca. Moduł wyrzucania elementów bezużytecznych próbuje zapewnić optymalną wydajność. Jeśli kolekcja w tle jest już w toku, Metoda wraca natychmiast.|  
  
## <a name="see-also"></a>Zobacz także

- [Tryby opóźnienia](latency.md)
- [Odzyskiwanie pamięci](index.md)
