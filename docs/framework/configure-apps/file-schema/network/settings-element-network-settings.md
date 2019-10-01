---
title: <settings>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697685"
---
# <a name="settings-element-network-settings"></a>\<settings >, element (Ustawienia sieci)
Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net?displayProperty=nameWithType>.  
  
[ **@no__t — 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Odbiornika HttpListener](httplistener-element-network-settings.md)|Dostosowuje parametry używane przez klasę <xref:System.Net.HttpListener>.|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Dostosowuje parametry żądania sieci Web.|  
|[If](ipv6-element-network-settings.md)|Włącza obsługę protokołu internetowego w wersji 6 (IPv6).|  
|[\<performanceCounter >, element (Ustawienia sieci)](performancecounter-element-network-settings.md)|Włącza liczniki wydajności sieci.|  
|[ServicePointManager](servicepointmanager-element-network-settings.md)|Konfiguruje połączenia z zasobami sieciowymi.|  
|[używając](socket-element-network-settings.md)|Określa, czy operacje gniazda używają portów zakończenia.|  
|[\<webProxyScript >, element (Ustawienia sieci)](webproxyscript-element-network-settings.md)|Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
