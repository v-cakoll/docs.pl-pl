---
title: Zasady pamięci podręcznej
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: afaa4389940bd16ee2685c2ed64fbec4626d96e1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193151"
---
# <a name="cache-policy"></a>Zasady pamięci podręcznej
Zasady pamięci podręcznej definiuje reguły, które są używane do ustalenia, czy można spełnić żądania przy użyciu pamięci podręcznej kopię żądanego zasobu. Aplikacje określić wymagania dotyczące pamięci podręcznej klienta dla daty utworzenia, ale zasady obowiązujące w pamięci podręcznej jest określana przez wymagania dotyczące pamięci podręcznej klienta, wygaśnięcia zawartości serwera oraz wymagania ponowną weryfikację serwera. Interakcja wymagania zasad i serwera pamięci podręcznej klienta zawsze skutkuje najbardziej umiarkowaną zasad pamięci podręcznej, aby mieć pewność, że najnowsza zawartość jest zwracana do aplikacji klienckiej.  
  
 Zasady pamięci podręcznej są oparte na lokalizacji lub na podstawie czasu. Zasady pamięci podręcznej na podstawie lokalizacji definiuje aktualności buforowanych wpisy podstawę, z którego można pobrać żądanego zasobu. Zasady pamięci podręcznej na podstawie czasu definiuje aktualność pozycji z pamięci podręcznej przy użyciu czasu, który został pobrany zasobu, nagłówki zwrócony z zasobów i bieżąca godzina. Większość aplikacji można użyć domyślne zasady pamięci podręcznej na podstawie czasu, która implementuje zasady buforowania, określona w dokumencie RFC 2616, dostępne pod adresem [ http://www.ietf.org ](http://www.ietf.org/).  
  
 Klas opisanych w poniższej tabeli służą do określania zasad pamięci podręcznej.  
  
|Nazwa klasy|Opis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Reprezentuje zasady oparte na lokalizacji i na podstawie czasu pamięci podręcznej dla zasobów żądana za pomocą <xref:System.Net.HttpWebRequest> obiektów.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Reprezentuje zasady oparte na lokalizacji pamięci podręcznej lub <xref:System.Net.Cache.RequestCacheLevel.Default> zasad pamięci podręcznej na podstawie czasu dla zasobów żądana za pomocą <xref:System.Net.WebRequest> obiektów.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Określa wartości używane do tworzenia opartych na czasie <xref:System.Net.Cache.HttpRequestCachePolicy> obiektów.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Określa wartości używane do tworzenia opartych na lokalizacji i oparte na czasie <xref:System.Net.Cache.HttpRequestCachePolicy> obiektów.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Określa wartości używane do tworzenia opartych na lokalizacji lub <xref:System.Net.Cache.RequestCacheLevel.Default> oparte na czasie <xref:System.Net.Cache.RequestCachePolicy> obiektów.|  
  
 Można zdefiniować zasady pamięci podręcznej dla wszystkich żądań przez aplikację lub poszczególnych żądań. Po określeniu zasad pamięci podręcznej z poziomu aplikacji i zasad pamięci podręcznej poziomie żądania zasad poziomie żądania jest używana. Można określić zasady pamięci podręcznej z poziomu aplikacji, programowo lub za pomocą aplikacji lub pliki konfiguracji maszyny. Aby uzyskać więcej informacji, zobacz [ \<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Aby utworzyć zasady pamięci podręcznej, należy utworzyć obiekt zasad przez utworzenie wystąpienia <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> klasy. Aby określić zasady, na żądanie, ustaw żądania <xref:System.Net.WebRequest.CachePolicy%2A> właściwości do obiektu zasad. Podczas programowego ustawiania zasad na poziomie aplikacji, ustawić <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> właściwości do obiektu zasad.  
  
 Aby uzyskać przykłady kodu, które pokazują tworzenie i używanie zasad buforowania, zobacz [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
