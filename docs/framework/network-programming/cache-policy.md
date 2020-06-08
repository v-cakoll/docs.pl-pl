---
title: Zasady pamięci podręcznej
description: Dowiedz się więcej na temat zasad pamięci podręcznej, zasad, które określają, czy żądanie może być spełnione przy użyciu buforowanej kopii żądanego zasobu.
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
ms.openlocfilehash: d63d2b6bf8426968d2120647c8ecea2b7602825a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502668"
---
# <a name="cache-policy"></a>Zasady pamięci podręcznej
Zasady pamięci podręcznej definiują reguły, które są używane do określenia, czy żądanie może być spełnione przy użyciu buforowanej kopii żądanego zasobu. Aplikacje określają wymagania dotyczące pamięci podręcznej klienta dla Aktualności, ale obowiązujące zasady pamięci podręcznej określają wymagania dotyczące pamięci podręcznej klienta, wymagania dotyczące wygaśnięcia zawartości serwera i wymagania dotyczące ponownego sprawdzania poprawności serwera. Interakcja z wymaganiami zasad i serwera pamięci podręcznej klienta zawsze polega na najbardziej nieodpowiedniej zasadzie pamięci podręcznej, aby zapewnić, że najnowsza zawartość jest zwracana do aplikacji klienckiej.  
  
 Zasady pamięci podręcznej są oparte na lokalizacji lub czasie. Zasady pamięci podręcznej oparte na lokalizacji określają świeżość buforowanych wpisów na podstawie lokalizacji, z której można pobrać żądany zasób. Zasady pamięci podręcznej oparte na czasie definiują świeżość buforowanych wpisów przy użyciu czasu pobrania zasobu, nagłówki zwrócone z zasobem i bieżący czas. Większość aplikacji może korzystać z domyślnych zasad pamięci podręcznej opartych na czasie, które implementują Zasady buforowania określone w dokumencie RFC 2616, dostępne w witrynie [Internet Engineering Task Force (IETF)](https://www.ietf.org/) .  
  
 Klasy opisane w poniższej tabeli służą do określania zasad pamięci podręcznej.  
  
|Nazwa klasy|Opis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Reprezentuje zasady pamięci podręcznej oparte na lokalizacji i czasie dla zasobów żądanych za pomocą <xref:System.Net.HttpWebRequest> obiektów.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Reprezentuje zasady pamięci podręcznej oparte na lokalizacji lub <xref:System.Net.Cache.RequestCacheLevel.Default> zasady pamięci podręcznej dla zasobów żądanych za pomocą <xref:System.Net.WebRequest> obiektów.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Określa wartości używane do tworzenia obiektów opartych na czasie <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Określa wartości używane do tworzenia obiektów opartych na lokalizacji i czasowych <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.RequestCacheLevel>|Określa wartości używane do tworzenia obiektów opartych na lokalizacji lub na <xref:System.Net.Cache.RequestCacheLevel.Default> podstawie czasu <xref:System.Net.Cache.RequestCachePolicy> .|  
  
 Można zdefiniować zasady pamięci podręcznej dla wszystkich żądań wykonywanych przez aplikację lub dla poszczególnych żądań. W przypadku określenia zasad pamięci podręcznej na poziomie aplikacji i zasad pamięci podręcznej na poziomie żądania są używane zasady na poziomie żądania. Zasady pamięci podręcznej na poziomie aplikacji można określić programowo lub przy użyciu plików konfiguracyjnych aplikacji lub komputera. Aby uzyskać więcej informacji, zobacz [ \<requestCaching> element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Aby utworzyć zasady pamięci podręcznej, należy utworzyć obiekt zasad, tworząc wystąpienie <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> klasy or. Aby określić zasady dla żądania, należy ustawić <xref:System.Net.WebRequest.CachePolicy%2A> Właściwość żądania na obiekt zasad. Konfigurując zasady na poziomie aplikacji programowo, należy ustawić <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> właściwość obiektu zasad.  
  
 Przykłady kodu, które demonstrują tworzenie i Używanie zasad pamięci podręcznej, można znaleźć [w temacie Konfigurowanie buforowania w aplikacjach sieciowych](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
