---
title: Zarządzanie pamięcią podręczną dla aplikacji sieciowych
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048874"
---
# <a name="cache-management-for-network-applications"></a>Zarządzanie pamięcią podręczną dla aplikacji sieciowych
W tym temacie i powiązanych z nim podtematach <xref:System.Net.HttpWebRequest>opisano <xref:System.Net.FtpWebRequest> buforowanie zasobów uzyskanych przy użyciu <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, i klas.  
  
 Pamięć podręczna zapewnia tymczasowe przechowywanie zasobów, które zostały wymagane przez aplikację. Jeśli aplikacja żąda tego samego zasobu więcej niż jeden raz, zasób może zostać zwrócony z pamięci podręcznej, unikając narzutu ponownego żądania go z serwera. Buforowanie może zwiększyć wydajność aplikacji, skracając czas wymagany do uzyskania żądanego zasobu. Buforowanie może również zmniejszyć ruch sieciowy, zmniejszając liczbę przejazdów do serwera. Podczas buforowania zwiększa wydajność, zwiększa ryzyko, że zasób zwrócony do aplikacji jest przestarzały, co oznacza, że nie jest identyczny z zasobem, który zostałby wysłany przez serwer, jeśli buforowanie nie były używane.  
  
 Buforowanie może zezwalać nieautoryzowanym użytkownikom lub procesom na odczytanie poufnych danych. Uwierzytelniona odpowiedź, która jest buforowana, może zostać pobrana z pamięci podręcznej bez dodatkowej autoryzacji. Jeśli buforowanie jest włączone, <xref:System.Net.WebRequest.CachePolicy%2A> zmień <xref:System.Net.Cache.RequestCacheLevel.BypassCache> <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> na lub wyłącz buforowanie dla tego żądania.  
  
 Ze względów bezpieczeństwa buforowanie **nie** jest zalecane w scenariuszach warstwy środkowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zasady pamięci podręcznej](cache-policy.md)  
 Wyjaśniono, co to jest zasada pamięci podręcznej i jak zdefiniować jedną.  
  
 [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)  
 Definiuje każdy typ zasad pamięci podręcznej opartych na lokalizacji dostępnych dla zasobów protokołu transferu hipertekstu (http i https).  
  
 [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)  
 W tym artykule opisano kryteria, które mogą służyć do dostosowywania zasad pamięci podręcznej opartych na czasie.  
  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)  
 W tym artykule opisano sposób programowego tworzenia zasad pamięci podręcznej i żądań korzystających z buforowania.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Net.Cache>  
 Definiuje typy i wyliczenia używane do definiowania <xref:System.Net.WebRequest>zasad <xref:System.Net.HttpWebRequest>pamięci <xref:System.Net.FtpWebRequest> podręcznej dla zasobów uzyskanych za pomocą programu , i klas.
