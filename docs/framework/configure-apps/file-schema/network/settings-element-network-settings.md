---
title: '&lt;ustawienia&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 87a944eca6ea4158f15c9911c6b13fd4d3c0921d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191956"
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;ustawienia&gt; — Element (ustawienia sieci)
Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[HttpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Dostosowuje parametrów używanych przez <xref:System.Net.HttpListener> klasy.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Dostosowuje parametry żądania sieci Web.|  
|[Protokół IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Włącza protokołu internetowego w wersji 6 (IPv6) pomocy technicznej.|  
|[\<performanceCounter >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Liczniki wydajności funkcji sieciowych umożliwia.|  
|[ServicePointManager —](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Służy do konfigurowania połączeń z zasobami sieciowymi.|  
|[Gniazda](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Określa, czy operacje gniazda używają portów.|  
|[\<webproxyscript — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Konfiguruje właściwości skryptu używanej do odnajdywania serwerów proxy sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[przestrzeni nazw System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Net?displayProperty=nameWithType>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
