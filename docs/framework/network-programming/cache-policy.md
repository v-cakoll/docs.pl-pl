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
ms.openlocfilehash: 2d3d85ebd80f417ebd0fa0e619097e15f2a6a39b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048777"
---
# <a name="cache-policy"></a>Zasady pamięci podręcznej
Zasady pamięci podręcznej definiuje reguły, które są używane do określenia, czy żądanie może być spełnione przy użyciu buforowanej kopii żądanego zasobu. Aplikacje określają wymagania pamięci podręcznej klienta dla świeżości, ale zasady skutecznej pamięci podręcznej zależy od wymagań pamięci podręcznej klienta, wymagań wygaśnięcia zawartości serwera i wymagań ponownego licencjonowania serwera. Interakcja zasad pamięci podręcznej klienta i wymagania serwera zawsze powoduje najbardziej konserwatywne zasady pamięci podręcznej, aby zapewnić, że najświeższa zawartość jest zwracana do aplikacji klienckiej.  
  
 Zasady pamięci podręcznej są oparte na lokalizacji lub na podstawie czasu. Zasady pamięci podręcznej oparte na lokalizacji definiują świeżość buforowanych wpisów na podstawie tego, skąd można zabrać żądany zasób. Zasady pamięci podręcznej oparte na czasie definiuje świeżość wpisów w pamięci podręcznej przy użyciu czasu, w której zasób został pobrany, nagłówków zwróconych z zasobem i bieżącej. Większość aplikacji może używać domyślnych zasad pamięci podręcznej opartych na czasie, która implementuje zasady buforowania określone w RFC 2616, dostępne w witrynie internetowej [Internet Engineering Task Force (IETF).](https://www.ietf.org/)  
  
 Klasy opisane w poniższej tabeli są używane do określania zasad pamięci podręcznej.  
  
|Nazwa klasy|Opis|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Reprezentuje oparte na lokalizacji i oparte na czasie <xref:System.Net.HttpWebRequest> zasady pamięci podręcznej dla zasobów wymaganych przy użyciu obiektów.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Reprezentuje zasady pamięci podręcznej <xref:System.Net.Cache.RequestCacheLevel.Default> oparte na lokalizacji lub oparte <xref:System.Net.WebRequest> na czasie zasady pamięci podręcznej dla zasobów wymaganych przy użyciu obiektów.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Określa wartości używane do tworzenia <xref:System.Net.Cache.HttpRequestCachePolicy> obiektów opartych na czasie.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Określa wartości używane do tworzenia obiektów opartych na lokalizacji i czasie. <xref:System.Net.Cache.HttpRequestCachePolicy>|  
|<xref:System.Net.Cache.RequestCacheLevel>|Określa wartości używane do tworzenia obiektów <xref:System.Net.Cache.RequestCacheLevel.Default> opartych <xref:System.Net.Cache.RequestCachePolicy> na lokalizacji lub opartych na czasie.|  
  
 Można zdefiniować zasady pamięci podręcznej dla wszystkich żądań złożonych przez aplikację lub dla poszczególnych żądań. Po określeniu zarówno zasad pamięci podręcznej na poziomie aplikacji, jak i zasad pamięci podręcznej na poziomie żądania, używana jest zasada na poziomie żądania. Zasady pamięci podręcznej na poziomie aplikacji można określić programowo lub przy użyciu plików konfiguracyjnych aplikacji lub komputera. Aby uzyskać więcej informacji, zobacz [ \<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Aby utworzyć zasady pamięci podręcznej, należy utworzyć obiekt zasad, tworząc wystąpienie <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> klasy. Aby określić zasady w żądaniu, <xref:System.Net.WebRequest.CachePolicy%2A> ustaw właściwość żądania na obiekt zasad. Podczas programowania programowania ustawiania zasad na <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> poziomie aplikacji ustaw właściwość na obiekt zasad.  
  
 Aby zapoznać się z przykładami kodu, które pokazują tworzenie i używanie zasad pamięci podręcznej, zobacz [Konfigurowanie buforowania w aplikacjach sieciowych](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [Konfigurowanie pamięci podręcznej w aplikacjach sieciowych](configuring-caching-in-network-applications.md)
