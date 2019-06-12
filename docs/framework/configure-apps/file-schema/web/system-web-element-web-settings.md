---
title: <system.web>, element (ustawienia internetowe)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 687398e47ad95e3234c29571eeeac0c9d2d83a39
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832789"
---
# <a name="systemweb-element-web-settings"></a>\<System.Web >, Element (ustawienia sieci Web)
Zawiera informacje o sposobie zarządzania zachowanie całego procesu w warstwie hostingu platformy ASP.NET.  
  
 \<Konfiguracja >  
\<System.Web >, Element (ustawienia sieci Web)  
  
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
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Określa ustawienia konfiguracji dla pul aplikacji usług IIS w plikach aspnet.config.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 `system.web` Elementu i jego podrzędny `applicationPool` element zostały dodane do programu .NET Framework, począwszy od programu .NET Framework 3.5 z dodatkiem SP1. Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowsze wersje w trybie zintegrowanym, ta kombinacja element umożliwia skonfigurowanie sposobu ASP.NET zarządza wątków i jak go umieszcza w kolejce żądań gdy ASP.NET jest hostowany w puli aplikacji usług IIS. Jeśli uruchamiasz [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowsze wersje w trybie klasycznym lub ISAPI, te ustawienia są ignorowane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować sposób działania całego procesu ASP.NET w pliku konfigurację aspnet.config ASP.NET znajduje się w puli aplikacji IIS. W przykładzie założono, że uruchomieniu usług IIS w zintegrowany tryb i że aplikacja używa .NET Framework 3.5 z dodatkiem SP1 lub nowszym. To zachowanie nie występuje w wersjach programu .NET Framework wcześniejszych niż .NET Framework 3.5 SP1. Wartości w przykładzie są wartości domyślne.  
  
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
|Plik walidacji||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz także

- [\<applicationPool >, Element (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
