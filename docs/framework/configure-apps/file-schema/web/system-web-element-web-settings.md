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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152844"
---
# <a name="systemweb-element-web-settings"></a>\<element> system.web (ustawienia sieci Web)
Zawiera informacje o tym, jak warstwa hostingu ASP.NET zarządza zachowaniem całego procesu.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;**\<>system.web**  
  
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
|[\<aplikacja>](applicationpool-element-web-settings.md)|Określa ustawienia konfiguracji pul aplikacji usług IIS w pliku aspnet.config.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracyjne](../configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  

Element `system.web` i jego `applicationPool` element podrzędny zostały dodane do .NET Framework w ramach .NET Framework 3.5 SP1. Po uruchomieniu usług IIS 7.0 lub nowszych wersji w trybie zintegrowanym ta kombinacja elementów umożliwia skonfigurowanie sposobu zarządzania wątkami ASP.NET i sposobu kolejkowania żądań, gdy ASP.NET jest hostowany w puli aplikacji usług IIS. Jeśli uruchomisz usługi IIS 7.0 lub nowsze w trybie klasycznym lub ISAPI, te ustawienia zostaną zignorowane.  
  
## <a name="example"></a>Przykład  

W poniższym przykładzie pokazano, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet.config, gdy ASP.NET jest hostowany w puli aplikacji usług IIS. W przykładzie przyjęto założenie, że usługi IIS są uruchomione w trybie zintegrowanym i że aplikacja korzysta z dodatku SP1 programu .NET Framework 3.5 lub nowszej. To zachowanie nie występuje w wersjach programu .NET Framework wcześniej niż dodatek SP1 .NET Framework 3.5. Wartości w przykładzie są wartościami domyślnymi.  
  
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
|Plik sprawdzania poprawności||  
|Może być pusty||  
  
## <a name="see-also"></a>Zobacz też

- [\<Element> aplikacji (ustawienia sieci Web)](applicationpool-element-web-settings.md)
