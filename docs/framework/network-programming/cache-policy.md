---
title: "Zasady pamięci podręcznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bafad45e6b6b546707c4f805f857e85549f0f071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cache-policy"></a>Zasady pamięci podręcznej
Zasady pamięci podręcznej definiuje reguły, które są używane do ustalenia, czy można spełnić żądania przy użyciu pamięci podręcznej kopię żądanego zasobu. Określ aplikacje, wymagania dotyczące pamięci podręcznej klienta dla świeżości, ale zasady skuteczne pamięci podręcznej jest określany przez wymagania dotyczące pamięci podręcznej klienta, wygaśnięcia zawartości serwera oraz wymagania dotyczące ponownego sprawdzania poprawności serwera. Interakcja wymagania zasad i serwera pamięci podręcznej klienta zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej, aby zapewnić, że najnowsza zawartość jest zwracana do aplikacji klienckiej.  
  
 Zasady pamięci podręcznej są oparte na lokalizacji lub oparte na czasie. Zasady oparte na lokalizacji pamięci podręcznej definiuje świeżości wpisów pamięci podręcznej podstawę, z którego można pobrać żądanego zasobu. Zasady na podstawie czasu pamięci podręcznej definiuje świeżości wpisów pamięci podręcznej przy użyciu czasu, który został pobrany zasobu, nagłówki zwrócił zasobu a bieżącą godziną. Większość aplikacji można użyć domyślne zasady na podstawie czasu pamięci podręcznej, która implementuje zasad buforowania określone w dokumencie RFC 2616 dostępne pod adresem [http://www.ietf.org](http://www.ietf.org/).  
  
 Klasy opisane w poniższej tabeli służą do określania zasad buforowania.  
  
|Nazwa klasy|Opis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Reprezentuje zasady oparte na lokalizacji i na podstawie czasu pamięci podręcznej dla zasobów żądana za pomocą <xref:System.Net.HttpWebRequest> obiektów.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Reprezentuje zasady oparte na lokalizacji pamięci podręcznej lub <xref:System.Net.Cache.RequestCacheLevel.Default> zasady na podstawie czasu pamięci podręcznej dla zasobów żądana za pomocą <xref:System.Net.WebRequest> obiektów.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Określa wartości użyte do utworzenia na podstawie czasu <xref:System.Net.Cache.HttpRequestCachePolicy> obiektów.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Określa wartości użyte do utworzenia na podstawie lokalizacji i na podstawie czasu <xref:System.Net.Cache.HttpRequestCachePolicy> obiektów.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Określa wartości użyte do utworzenia na podstawie lokalizacji lub <xref:System.Net.Cache.RequestCacheLevel.Default> oparte na czasie <xref:System.Net.Cache.RequestCachePolicy> obiektów.|  
  
 Można zdefiniować zasady pamięci podręcznej dla wszystkich żądań przez aplikację lub poszczególnych żądań. Po określeniu zarówno zasady pamięci podręcznej z poziomu aplikacji, jak i zasady pamięci podręcznej poziomie żądania zasad żądania poziomu jest używany. Można określić zasady pamięci podręcznej z poziomu aplikacji programowo lub za pomocą aplikacji lub plików konfiguracji maszyny. Aby uzyskać więcej informacji, zobacz [ \<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Aby utworzyć zasady pamięci podręcznej, należy utworzyć obiekt zasad przez utworzenie wystąpienia <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> klasy. Aby określić zasady żądania, ustaw żądania <xref:System.Net.WebRequest.CachePolicy%2A> właściwości do obiektu zasad. Jeśli ustawienie zasad na poziomie aplikacji programowo, należy skonfigurować <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> właściwości do obiektu zasad.  
  
 Aby uzyskać przykłady kodu, które przedstawiają Tworzenie zasad i korzystanie z pamięci podręcznej, zobacz [Konfigurowanie buforowanie w aplikacjach sieci](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
