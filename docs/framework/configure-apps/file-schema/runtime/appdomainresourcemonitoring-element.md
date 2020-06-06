---
title: <appDomainResourceMonitoring> Element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154379"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring> Element
Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domeny aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Zbierane są statystyki dotyczące monitorowania zasobów domeny aplikacji.|  
|`false`|Nie są zbierane statystyki dotyczące monitorowania zasobów domeny aplikacji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Monitorowanie zasobów domeny aplikacji jest dostępne za pomocą klasy domeny aplikacji zarządzanej, interfejsu hosta [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń systemu Windows (ETW). Po włączeniu monitorowania statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały czas trwania procesu.  
  
 Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć monitorowanie zasobów domeny aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
