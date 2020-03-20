---
title: <remove>, element dla webRequestModules (ustawienia sieci)
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
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154728"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a>\<usuń element> dla webRequestModules (Ustawienia sieciowe)
Usuwa niestandardowy moduł żądania sieci Web z aplikacji.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**
  
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
|[webRequestModules (WebRequestModules)](webrequestmodules-element-network-settings.md)|Określa moduły, za pomocą których mają być wymagane informacje od hostów sieciowych.|  
  
## <a name="remarks"></a>Uwagi  
 Element `remove` usuwa zarejestrowany moduł żądania sieci Web dla określonego prefiksu URI.  
  
 Wartość atrybutu `prefix` powinna być znakami wiodącymi prawidłowego identyfikatora URI , na przykład " "`http`lub "`http://www.contoso.com`".  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  

Poniższy przykład usuwa istniejący moduł żądania sieci Web dla protokołu HTTP, a `www.contoso.com`następnie rejestruje nowy niestandardowy moduł żądania sieci Web dla żądań HTTP do .
  
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

- <xref:System.Net.WebRequest>
- [Schemat ustawień sieci](index.md)
