---
title: <appDomainResourceMonitoring>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154379"
---
# <a name="appdomainresourcemonitoring-element"></a>\<element>> monitorowania> appDomainResource
Nakazuje środowiska wykonawczego do zbierania statystyk dotyczących wszystkich domen aplikacji w procesie przez cały okres procesu.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>monitorowania aplikacji DomaineResourceMonitoring**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko wykonawcze zbiera statystyki monitorowania zasobów domeny aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Zbierane są statystyki monitorowania zasobów domeny aplikacji.|  
|`false`|Statystyki monitorowania zasobów domeny aplikacji nie są zbierane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Monitorowanie zasobów domeny aplikacji jest dostępne za pośrednictwem klasy domeny aplikacji zarządzanej, hostingu interfejsu [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń dla systemu Windows (ETW). Gdy monitorowanie jest włączone, statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały okres procesu.  
  
 Aby włączyć monitorowanie z kodu <xref:System.AppDomain.MonitoringIsEnabled%2A> zarządzanego, należy użyć właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 i nowszych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak włączyć monitorowanie zasobów domeny aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
