---
title: '&lt;Dodaj&gt; (ustawienia sieciowe) webRequestModules — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 921f5f2bfda1a19d022d3f3f4131e3653fd17ea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742793"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a>&lt;Dodaj&gt; (ustawienia sieciowe) webRequestModules — Element
Dodaje niestandardowego modułu żądania sieci Web do aplikacji.  
  
 \<Konfiguracja >  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`prefix`|Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.|  
|`type`|Nazwa typu w pełni kwalifikowana (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), rozdzielone przecinkami, który implementuje ten moduł żądania sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[webRequestModules —](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły służące do żądania informacji z hostów w sieci.|  
  
## <a name="remarks"></a>Uwagi  
 `prefix` Atrybut definiuje prefiks identyfikatora URI, który używa określonego modułu żądania sieci Web. Moduły żądania sieci Web zwykle są rejestrowane do obsługi określonego protokołu, na przykład HTTP lub FTP, ale można zarejestrować do obsługi żądania do określonego serwera lub na serwerze.  
  
 Moduł żądania sieci Web jest tworzona podczas zgodny prefiks identyfikatora URI jest przekazywana do <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.  
  
 Wartość `prefix` atrybutu powinna być pierwszych znaków z prawidłowym identyfikatorem URI — na przykład "http" lub "http://www.contoso.com".  
  
 Wartość `type` atrybutu powinna być prawidłową nazwą typu i odpowiadającą jej nazwą zestawu, rozdzielonych przecinkami.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje niestandardowego modułu żądania sieci Web do obsługi protokołu HTTP. Wartości należy zastąpić wersję i PublicKeyToken przy użyciu prawidłowych wartości dla określonego modułu.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
