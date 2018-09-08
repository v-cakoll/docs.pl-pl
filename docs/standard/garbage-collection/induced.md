---
title: Wywołane kolekcje
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69590b0efc924132d149621c135ef0816cac7d1e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192551"
---
# <a name="induced-collections"></a>Wywołane kolekcje
W większości przypadków moduł odśmiecania pamięci może określić najlepszy czas na wykonywanie odśmiecania i należy pozwolić mu działać niezależnie. Istnieją rzadkich sytuacjach, gdy wymuszona Kolekcja może zwiększyć wydajność aplikacji. W takich przypadkach można wywołać wyrzucanie elementów bezużytecznych, za pomocą <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody w celu wymuszenia wyrzucania elementów bezużytecznych.  
  
 Użyj <xref:System.GC.Collect%2A?displayProperty=nameWithType> metody, gdy istnieje znaczne zmniejszenie ilości pamięci używanej w określonym miejscu w kodzie twojej aplikacji. Na przykład jeśli aplikacja używa skomplikowanego okna dialogowego zawierającego kilka formantów, wywołanie <xref:System.GC.Collect%2A> po zamknięciu okno dialogowe może zwiększyć wydajność przez natychmiastowe odzyskanie pamięci używanej przez okno dialogowe. Upewnij się, że aplikacja jest nie wykonuje wyrzucanie elementów bezużytecznych zbyt często, ponieważ może to obniżyć wydajność, jeśli wyrzucanie elementów bezużytecznych stara się odzyskać obiekty w czasie optymalnej. Możesz podać <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> wartość wyliczenia do <xref:System.GC.Collect%2A> metodę zbierania tylko wtedy, gdy kolekcja będzie wydajna, zgodnie z opisem w następnej sekcji.  
  
## <a name="gc-collection-mode"></a>Tryb kolekcji GC  
 Możesz użyć jednej z <xref:System.GC.Collect%2A?displayProperty=nameWithType> przeciążenia metody, które obejmuje <xref:System.GCCollectionMode> wartość, aby określić zachowanie dla wymuszonej kolekcji w następujący sposób.  
  
|`GCCollectionMode` Wartość|Opis|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Używa domyślnego ustawienia kolekcji wyrzucania elementów dla uruchomionej wersji .NET.|  
|<xref:System.GCCollectionMode.Forced>|Wymusza wyrzucanie elementów bezużytecznych natychmiast. Jest to równoważne z wywoływaniem <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenia. Wynikiem blokującym cały zbiór wszystkich generacji.<br /><br /> Możesz również skompaktować stertę dużego obiektu przez ustawienie <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwość <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> przed wymuszeniem natychmiastowej pełnej blokowania wyrzucania elementów bezużytecznych.|  
|<xref:System.GCCollectionMode.Optimized>|Włącza moduł odśmiecania pamięci w celu ustalenia, czy bieżąca godzina jest optymalna do odzyskania obiektów.<br /><br /> Moduł zbierający elementy bezużyteczne mógł określić, że kolekcja nie będzie wystarczająco wydajna, aby mieć uzasadnienie, w którym to przypadku je odzyska obiektów.|  
  
## <a name="background-or-blocking-collections"></a>Tło lub kolekcje blokowania  
 Możesz wywołać <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> przeciążenia metody, aby określić, czy wywołana kolekcja powoduje blokadę, czy nie. Typ wykonywanej kolekcji zależy od kombinacji metody `mode` i `blocking` parametrów. `mode` jest elementem członkowskim <xref:System.GCCollectionMode> wyliczenia, a `blocking` jest <xref:System.Boolean> wartość. Poniższa tabela podsumowuje interakcje `mode` i `blocking` argumentów.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> lub <xref:System.GCCollectionMode.Default>|Blokowanie kolekcji jest wykonywane tak szybko, jak to możliwe. Jeśli zbieranie w tle jest w toku i generowania jest równa 0 lub 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> metoda natychmiast wyzwala zbieranie blokujące i zwraca po zakończeniu zbierania. Jeśli zbieranie w tle jest w toku i `generation` parametru wynosi 2, metoda czeka, dopóki nie zakończy bezużytecznych w tle, wyzwala zbieranie blokujące 2. generacji, a następnie zwraca.|Kolekcja jest wykonywana tak szybko, jak to możliwe. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda żąda kolekcja tła, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokowania. Jeśli zbieranie w tle jest już w toku, metoda zwraca natychmiast.|  
|<xref:System.GCCollectionMode.Optimized>|Blokowanie kolekcji mogą być wykonywane w zależności od stanu modułu odśmiecania pamięci i `generation` parametru. Wyrzucanie elementów bezużytecznych stara się zapewnić optymalną wydajność.|Kolekcja może być wykonywana w zależności od stanu modułu odśmiecania pamięci. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Metoda żąda kolekcja tła, ale nie jest to gwarantowane; w zależności od okoliczności nadal może być wykonywana kolekcja blokowania. Wyrzucanie elementów bezużytecznych stara się zapewnić optymalną wydajność. Jeśli zbieranie w tle jest już w toku, metoda zwraca natychmiast.|  
  
## <a name="see-also"></a>Zobacz także

- [Tryby opóźnienia](../../../docs/standard/garbage-collection/latency.md)  
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
