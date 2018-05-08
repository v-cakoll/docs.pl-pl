---
title: Wywołane kolekcje
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 436953782049800e89298932278af4e450fc10de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="induced-collections"></a>Wywołane kolekcje
W większości przypadków moduł garbage collector można określić najlepszy moment na wykonać kolekcji, a należy udostępnić go uruchomić niezależnie. Istnieje rzadkich sytuacji po wymuszonym kolekcji może zwiększyć wydajność aplikacji. Wyrzucanie elementów bezużytecznych w tych przypadkach może wywołać przy użyciu <xref:System.GC.Collect%2A?displayProperty=nameWithType> metodę wymuszania wyrzucania elementów bezużytecznych.  
  
 Użyj <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody po znaczące zmniejszenie ilości pamięci używanej w określonym w kodzie aplikacji. Na przykład, jeśli aplikacja używa złożonych okno dialogowe ma kilka formantów, wywoływania <xref:System.GC.Collect%2A> zamknięcia okna dialogowego może zwiększyć wydajność przez natychmiast odzyskiwanie pamięci używane przez okno dialogowe. Upewnij się, że aplikacja to nie powoduje wyrzucanie elementów bezużytecznych zbyt często, ponieważ, która może obniżyć wydajność, jeśli moduł zbierający elementy bezużyteczne podejmuje próbę odzyskania obiektów w czasie — optymalne. Możesz podać <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> wartości wyliczenia <xref:System.GC.Collect%2A> metody do zbierania tylko wtedy, gdy kolekcja będzie produktywności, zgodnie z opisem w następnej sekcji.  
  
## <a name="gc-collection-mode"></a>Tryb kolekcji GC  
 Można użyć jednej z <xref:System.GC.Collect%2A?displayProperty=nameWithType> przeciążenia metody, które obejmuje <xref:System.GCCollectionMode> wartość, aby określić zachowanie dla kolekcji wymuszone w następujący sposób.  
  
|`GCCollectionMode` Wartość|Opis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Używa domyślnego ustawienia kolekcji pamięci dla uruchomionej wersji platformy .NET.|  
|<xref:System.GCCollectionMode.Forced>|Wyrzucanie elementów bezużytecznych wymusza natychmiastową. Jest to odpowiednik wywołania <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenia. Wynikiem pełnej kolekcji blokowania wszystkich generacji.<br /><br /> Można również compact sterty dużego obiektu przez ustawienie <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> przed wymuszeniem natychmiastowego pełnego blokowania wyrzucanie elementów bezużytecznych.|  
|<xref:System.GCCollectionMode.Optimized>|Włącza moduł garbage collector określić, czy bieżący czas jest optymalna odzyskiwanie obiektów.<br /><br /> Moduł zbierający elementy bezużyteczne mógł określić, że kolekcji nie będzie produktywności uzasadnione, w którym to przypadku zwróci bez odzyskiwanie obiektów.|  
  
## <a name="background-or-blocking-collections"></a>Tło lub blokowanie kolekcji  
 Możesz wywołać <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> przeciążenie metody, aby określić, czy czy nie blokuje wywołanych kolekcji. Typ kolekcji wykonać zależy od na kombinacji metody `mode` i `blocking` parametrów. `mode` jest elementem członkowskim <xref:System.GCCollectionMode> wyliczenia, i `blocking` jest <xref:System.Boolean> wartość. W poniższej tabeli przedstawiono interakcje z `mode` i `blocking` argumentów.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> lub <xref:System.GCCollectionMode.Default>|Blokowanie kolekcji jest wykonywane tak szybko, jak to możliwe. Jeśli pamięci w tle jest w toku i generowanie jest równa 0 lub 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> metoda natychmiast wyzwala blokowania kolekcji i zwraca po zakończeniu kolekcji. Jeśli pamięci w tle jest w toku i `generation` parametr to 2, czeka metody do momentu pamięci w tle została zakończona, wyzwala blokowania kolekcji generacji 2, a następnie zwraca.|Kolekcja jest wykonywane tak szybko, jak to możliwe. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda żąda pamięci w tle, ale nie gwarantuje; w pewnych okolicznościach blokowania kolekcji nadal może być wykonana. Jeśli pamięci w tle jest już w toku, metoda zwraca natychmiast.|  
|<xref:System.GCCollectionMode.Optimized>|Blokowanie kolekcji może być wykonana, w zależności od stanu modułu zbierającego elementy bezużyteczne i `generation` parametru. Moduł zbierający elementy bezużyteczne próbuje zapewnić optymalną wydajność.|Kolekcja może być wykonana, w zależności od stanu moduł garbage collector. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda żąda pamięci w tle, ale nie gwarantuje; w pewnych okolicznościach blokowania kolekcji nadal może być wykonana. Moduł zbierający elementy bezużyteczne próbuje zapewnić optymalną wydajność. Jeśli pamięci w tle jest już w toku, metoda zwraca natychmiast.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tryby opóźnienia](../../../docs/standard/garbage-collection/latency.md)  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
