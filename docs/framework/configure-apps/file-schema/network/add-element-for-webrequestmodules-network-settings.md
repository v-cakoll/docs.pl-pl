---
title: <add>, element dla webRequestModules (ustawienia sieci)
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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155027"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<dodaj element> dla webRequestModules (Ustawienia sieciowe)
Dodaje niestandardowy moduł żądania sieci Web do aplikacji.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**

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
|`type`|W pełni kwalifikowana nazwa typu <xref:System.Type.FullName%2A> (wskazana przez właściwość) <xref:System.Reflection.Assembly.FullName%2A> i nazwa zestawu (wskazana przez właściwość), oddzielona przecinkiem, która implementuje ten moduł żądania sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[webRequestModules (WebRequestModules)](webrequestmodules-element-network-settings.md)|Określa moduły, za pomocą których mają być wymagane informacje od hostów sieciowych.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybut `prefix` definiuje prefiks identyfikatora URI, który używa określonego modułu żądania sieci Web. Moduły żądań sieci Web są zazwyczaj rejestrowane do obsługi określonego protokołu, takiego jak HTTP lub FTP, ale mogą być zarejestrowane do obsługi żądania do określonego serwera lub ścieżki na serwerze.  
  
 Moduł żądania sieci Web jest tworzony, gdy prefiks dopasowania identyfikatora URI jest przekazywany do <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.  
  
 Wartość atrybutu `prefix` powinna być znakami wiodącymi prawidłowego identyfikatora URI. Na przykład: `http` lub `http://www.contoso.com`.
  
 Wartość atrybutu `type` powinna być prawidłową nazwą typu i odpowiednią nazwą zestawu, oddzieloną przecinkiem.
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje niestandardowy moduł żądania sieci Web dla protokołu HTTP. Należy zastąpić wartości dla Version i PublicKeyToken z poprawnymi wartościami dla określonego modułu.  
  
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

- <xref:System.Net.WebRequest>
- [Schemat ustawień sieci](index.md)
