---
title: "&lt;appdomainresourcemonitoring —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58caa7458d96ca7bb9088b607a83b2d6be667cae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appdomainresourcemonitoring —&gt; — Element
Powoduje, że środowiska uruchomieniowego w celu zbierania statystyk we wszystkich domenach aplikacji w trakcie cyklu życia procesu.  
  
 \<Konfiguracja >  
\<Runtime >  
\<appdomainresourcemonitoring — >  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domen aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Statystyki dotyczące monitorowania zasobów domen aplikacji są zbierane.|  
|`false`|Statystyki dotyczące monitorowania zasobów domen aplikacji nie są zbierane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Monitorowanie zasobów domen aplikacji jest dostępna za pośrednictwem klasy domeny zarządzanej aplikacji, hostingu [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interfejsu i śledzenie zdarzeń systemu Windows (ETW). Gdy jest włączone monitorowanie, statystyki są zbierane dla wszystkich domen aplikacji w trakcie cyklu życia procesu.  
  
 Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób włączania monitorowania zasobów domen aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
