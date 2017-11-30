---
title: "Zarządzanie pamięci podręcznej dla aplikacji sieciowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b960942d17e402b333354bbd932cf63d11b1209f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cache-management-for-network-applications"></a>Zarządzanie pamięci podręcznej dla aplikacji sieciowych
Ten temat i jego tematy pokrewne podrzędne opisują buforowanie zasobów uzyskany przy użyciu <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.  
  
 Pamięć podręczna zawiera magazyn tymczasowy zasobów, które zostały żądany przez aplikację. Jeśli aplikacja żąda tego samego zasobu więcej niż raz, zasób może być zwracany z pamięci podręcznej umożliwia uniknięcie przeciążenia ponownie żąda od serwera. Buforowanie może poprawić wydajność aplikacji, skracając czas wymagany do pobrania żądanego zasobu. Buforowanie można także zmniejszyć obciążenie sieci dzięki zmniejszeniu liczby rund do serwera. Gdy buforowanie zwiększa wydajność, zwiększa ryzyko, że zasób zwracana do aplikacji jest przestarzała, co oznacza, że nie jest identyczny zasobem, który będzie zostało wysłane przez serwer, jeśli buforowanie nie były używane.  
  
 Buforowanie mogą zezwolić nieautoryzowanymi użytkownikami lub procesami, które można odczytać danych poufnych. Uwierzytelnioną buforowaną odpowiedź mogą pobrać z pamięci podręcznej bez dodatkowych autoryzacji. Jeśli jest włączone buforowanie, zmień <xref:System.Net.WebRequest.CachePolicy%2A> do <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> wyłączenie buforowania dla tego żądania.  
  
 Ze względów bezpieczeństwa buforowanie jest **nie** zalecane w przypadku scenariuszy warstwy środkowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 Wyjaśniono, jakie zasady pamięci podręcznej oraz sposób definiowania jeden.  
  
 [Zasady oparte na lokalizacji pamięci podręcznej](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Definiuje każdego typu zasad na podstawie lokalizacji pamięci podręcznej dostępnych zasobów Hypertext Transfer Protocol (protokół http i https).  
  
 [Zasady na podstawie czasu pamięci podręcznej](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Zawiera opis kryteriów, które mogą służyć do konfigurowania zasad na podstawie czasu pamięci podręcznej.  
  
 [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Opisuje sposób programowego tworzenia zasady pamięci podręcznej i żądania, które używają buforowania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Net.Cache>  
 Określa typy oraz wyliczenia używane do definiowania zasad buforowania zasobów uzyskany przy użyciu <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.
