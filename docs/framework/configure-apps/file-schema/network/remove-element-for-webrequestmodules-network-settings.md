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
ms.openlocfilehash: 20a586e945a889d1fd8a8d4c5c09c8b790c56fc3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664015"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a>\<Usuń element > dla webRequestModules (Ustawienia sieci)
Usuwa niestandardowy moduł żądania sieci Web z aplikacji.  
  
 \<> konfiguracji  
\<system.net>  
\<webRequestModules>  
\<remove>  
  
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
|`prefix`|Prefiks identyfikatora URI dla żądań obsłużonych przez ten moduł żądania sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Element usuwa zarejestrowany moduł żądania sieci Web dla określonego prefiksu URI.  
  
 Wartość `prefix` atrybutu powinna być wiodącymi znakami prawidłowego identyfikatora URI — na przykład "`http`" lub "`http://www.contoso.com`".  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  

Poniższy przykład usuwa istniejący moduł żądania sieci Web dla protokołu HTTP, a następnie rejestruje nowy niestandardowy moduł żądania sieci Web dla żądań `www.contoso.com`http.
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebRequest>
- [Schemat ustawień sieci](index.md)
