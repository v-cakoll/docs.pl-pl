---
title: Odzyskiwanie pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931536"
---
# <a name="garbage-collection"></a>Odzyskiwanie pamięci
. Moduł wyrzucania elementów bezużytecznych dla NET zarządza alokacją i zwolnieniem pamięci dla aplikacji. Zawsze podczas tworzenia nowego obiektu środowisko uruchomieniowe języka wspólnego przydziela pamięć dla obiektu z zarządzanego stosu. Tak długo, jak przestrzeń adresowa jest dostępna w zarządzanym stosie, środowisko wykonawcze w dalszym ciągu przydziela miejsce dla nowych obiektów. Jednak pamięć nie jest nieskończona. Ostatecznie moduł zbierający elementy bezużyteczne musi wykonać kolekcję w celu zwolnienia pamięci. Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały. Gdy moduł zbierający elementy bezużyteczne wykonuje kolekcję, sprawdza czy istnieją obiekty na zarządzanym stosie, które nie są już używane przez aplikację, i wykonuje niezbędne operacje do odzyskania ich pamięci.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Podstawy dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/fundamentals.md)|Opisuje jak działa wyrzucanie elementów bezużytecznych, jak obiekty są przydzielane na zarządzanym stosie oraz inne podstawowe pojęcia.|  
|[Odzyskiwanie pamięci i wydajność](../../../docs/standard/garbage-collection/performance.md)|Opisuje testy wydajności, które można użyć do diagnozowania problemów z wydajnością wyrzucania elementów bezużytecznych.|  
|[Wywołane kolekcje](../../../docs/standard/garbage-collection/induced.md)|Opisuje, jak sprawić, aby nastąpiło wyrzucanie elementów bezużytecznych.|  
|[Tryby opóźnienia](../../../docs/standard/garbage-collection/latency.md)|Opisuje tryby, które określają ingerencję operacji wyrzucania elementów bezużytecznych.|  
|[Optymalizacja udostępnionej usługi hostingu internetowego](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Opisuje, jak zoptymalizować wyrzucanie elementów bezużytecznych na serwerach współużytkowanych przez kilka małych witryn sieci Web.|  
|[Powiadomienia dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/notifications.md)|Opisuje, jak określić kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zostało ono ukończone.|  
|[Monitorowanie zasobów domen aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Opisuje, jak monitorować wykorzystanie procesora i pamięci przez domenę aplikacji.|  
|[Słabe odwołania](../../../docs/standard/garbage-collection/weak-references.md)|Opisuje funkcje, które pozwalają modułowi zbierającemu elementy bezużyteczne na zbieranie obiektu, wciąż zezwalając aplikacjom na dostęp do tego obiektu.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz także

- [Oczyszczanie zasobów niezarządzanych](../../../docs/standard/garbage-collection/unmanaged.md)
