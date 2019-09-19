---
title: Zarządzanie pamięcią podręczną dla aplikacji sieciowych
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048874"
---
# <a name="cache-management-for-network-applications"></a>Zarządzanie pamięcią podręczną dla aplikacji sieciowych
Ten temat i powiązane z nim tematy zawierają opis buforowania zasobów uzyskanych przy użyciu <xref:System.Net.WebClient>klas <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> .  
  
 Pamięć podręczna zapewnia tymczasowy magazyn zasobów, które zostały zlecone przez aplikację. Jeśli aplikacja żąda tego samego zasobu więcej niż jeden raz, można zwrócić zasób z pamięci podręcznej, unikając ponownego zażądania od serwera. Buforowanie może zwiększyć wydajność aplikacji przez skrócenie czasu wymaganego do uzyskania żądanego zasobu. Buforowanie może również zmniejszyć ruch sieciowy, zmniejszając liczbę podróży do serwera. Buforowanie zwiększa wydajność, ale zwiększa ryzyko, że zasób zwrócony do aplikacji jest nieodświeżony, co oznacza, że nie jest on identyczny z zasobem, który został wysłany przez serwer, Jeśli buforowanie nie było używane.  
  
 Buforowanie może umożliwić nieautoryzowanym użytkownikom lub procesom odczytywanie poufnych danych. Uwierzytelniona odpowiedź w pamięci podręcznej może być pobierana z pamięci podręcznej bez dodatkowej autoryzacji. Jeśli buforowanie jest włączone, Zmień na <xref:System.Net.WebRequest.CachePolicy%2A> <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> , aby wyłączyć buforowanie dla tego żądania.  
  
 Ze względu na kwestie bezpieczeństwa buforowanie **nie** jest zalecane w przypadku scenariuszy warstwy środkowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zasady pamięci podręcznej](cache-policy.md)  
 Wyjaśnia, co to są zasady pamięci podręcznej i jak je definiować.  
  
 [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)  
 Definiuje każdy typ zasad pamięci podręcznej opartych na lokalizacji dostępnych dla zasobów protokołu HTTP i https.  
  
 [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)  
 Opisuje kryteria, których można użyć do dostosowania zasad pamięci podręcznej opartej na czasie.  
  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)  
 Opisuje sposób programistycznego tworzenia zasad pamięci podręcznej i żądań korzystających z buforowania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Net.Cache>  
 Definiuje typy i wyliczenia używane do definiowania zasad pamięci podręcznej dla zasobów uzyskanych <xref:System.Net.WebRequest>przy <xref:System.Net.HttpWebRequest>użyciu klas <xref:System.Net.FtpWebRequest> , i.
