---
title: '&lt;System.Web&gt; elementu (ustawienia sieci Web)'
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7527ee9e7528a0da47529bae93e8112705e03a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755165"
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;System.Web&gt; elementu (ustawienia sieci Web)
Zawiera informacje o zarządzaniu warstwy hostingu ASP.NET zachowanie całego procesu.  
  
 \<Konfiguracja >  
\<System.Web > elementu (ustawienia sieci Web)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<ApplicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Określa ustawienia konfiguracji dla pul aplikacji usług IIS w pliku konfigurację aspnet.config.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 `system.web` Elementu i jego podrzędny `applicationPool` element zostały dodane do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszy w trybie zintegrowanym, ta kombinacja element umożliwia skonfigurowanie zarządzaniu wątków ASP.NET i jak go kolejki żądań ASP.NET jest obsługiwany w puli aplikacji usług IIS. Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszy w trybie klasycznym lub ISAPI, te ustawienia są ignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można skonfigurować sposób działania całego procesu ASP.NET w pliku konfigurację aspnet.config ASP.NET znajduje się w puli aplikacji usług IIS. W przykładzie założono, że usługi IIS działają w zintegrowanym trybu i że aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszym. To zachowanie nie występuje w wersjach [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wcześniejszy niż [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]. Wartości w tym przykładzie są wartościami domyślnymi.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|Przestrzeń nazw||  
|Nazwa schematu||  
|Sprawdzanie poprawności pliku||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz też  
 [\<applicationPool > elementu (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
