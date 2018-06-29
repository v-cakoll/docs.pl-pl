---
title: '&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 40eda14d4d578f10a77aa06843abd48f58c55f6a
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37073024"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a>&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)
Usuwa niestandardowego modułu żądania sieci Web z aplikacji.  
  
 \<Konfiguracja >  
\<system.net>  
\<webRequestModules>  
\<Usuń >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`prefix`|Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[webRequestModules —](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły służące do żądania informacji z hostów w sieci.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Element usuwa zarejestrowanego modułu żądania sieci Web dla określonego prefiksu identyfikatora URI.  
  
 Wartość `prefix` atrybutu powinna być pierwszych znaków z prawidłowym identyfikatorem URI — na przykład "http" lub "`http://www.contoso.com` ".  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa istniejący moduł żądania sieci Web do obsługi protokołu HTTP, a następnie rejestruje nowego niestandardowego sieci Web żądania modułu HTTP żądań www.contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebRequest>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
