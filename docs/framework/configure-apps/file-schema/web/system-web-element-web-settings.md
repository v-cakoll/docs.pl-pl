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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699092"
---
# <a name="systemweb-element-web-settings"></a>@no__t -0system. Web > element (Ustawienia sieci Web)
Zawiera informacje o sposobie zarządzania zachowaniem całego procesu przez warstwę hostingu ASP.NET.  
  
[ **@no__t — 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **@no__t -3system. web >**  
  
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
|[@no__t — 1applicationPool >](applicationpool-element-web-settings.md)|Określa ustawienia konfiguracji dla pul aplikacji usług IIS w pliku aspnet. config.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[@no__t — 1configuration >](../configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  

Element `system.web` i jego element podrzędny `applicationPool` zostały dodane do .NET Framework w ramach .NET Framework 3,5 z dodatkiem SP1. W przypadku uruchamiania usług IIS 7,0 lub nowszych w trybie zintegrowanym Ta kombinacja elementów umożliwia skonfigurowanie sposobu, w jaki program ASP.NET zarządza wątkami i w jaki sposób kolejki są wysyłane w puli aplikacji usług IIS. W przypadku uruchomienia usług IIS 7,0 lub nowszych w trybie klasycznym lub ISAPI te ustawienia zostaną zignorowane.  
  
## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet. config, gdy ASP.NET jest hostowany w puli aplikacji IIS. W przykładzie przyjęto założenie, że usługi IIS działają w trybie zintegrowanym i że aplikacja korzysta z .NET Framework 3,5 z dodatkiem SP1 lub nowszej wersji. To zachowanie nie występuje w wersjach .NET Framework starszych niż .NET Framework 3,5 SP1. Wartości w przykładzie są wartościami domyślnymi.  
  
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
|Może być puste||  
  
## <a name="see-also"></a>Zobacz także

- [\<applicationPool >, element (Ustawienia sieci Web)](applicationpool-element-web-settings.md)
