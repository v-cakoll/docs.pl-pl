---
title: '&lt;Wyczyść&gt; elementu webRequestModules — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d89fbc757198f25219b8051bf77dbdeea0cef53
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752731"
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a>&lt;Wyczyść&gt; elementu webRequestModules — (ustawienia sieciowe)
Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.  
  
 \<Konfiguracja >  
\<system.net>  
\<webRequestModules>  
\<Wyczyść >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[webRequestModules —](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły służące do żądania informacji z hostów w sieci.|  
  
## <a name="remarks"></a>Uwagi  
 `clear` Elementu spowoduje usunięcie wszystkich zarejestrowanych modułów żądania sieci Web, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje wyczyszczenie wszystkich modułów żądania sieci Web, a następnie rejestruje moduł żądania sieci Web do obsługi protokołu HTTP.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
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
