---
title: '&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2e224f710a1f344623440f29c2c6e0e9bd661e
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072517"
---
# <a name="ltproxygt-element-network-settings"></a>&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)
Definiuje serwera proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy — >  
\<Serwer proxy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`autoDetect`|Określa, czy serwer proxy jest wykrywany automatycznie. Wartość domyślna to `unspecified`.|  
|`bypassonlocal`|Określa, czy serwer proxy jest pomijana dla zasobów lokalnych. Zasobów lokalnych obejmują serwer lokalny (`http://localhost`, `http://loopback`, lub `http://127.0.0.1`) i identyfikator URI bez kropki (`http://webserver`). Wartość domyślna to `unspecified`.|  
|`proxyaddress`|Określa identyfikator URI do użycia serwera proxy.|  
|`scriptLocation`|Określa lokalizację skryptu konfiguracji.|  
|`usesystemdefault`|Określa, czy ustawienia serwera proxy programu Internet Explorer. Jeśli ustawiono `true`, kolejne atrybuty spowoduje zastąpienie ustawień serwera proxy programu Internet Explorer. Wartość domyślna to `unspecified`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy —](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).|  
  
## <a name="text-value"></a>Wartość tekstowa  
  
## <a name="remarks"></a>Uwagi  
 `proxy` Element definiuje serwera proxy dla aplikacji. W przypadku braku tego elementu z pliku konfiguracji programu .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.  
  
 Wartość `proxyaddress` atrybutu powinna być poprawnie sformułowanym wskaźnik URI (Uniform Resource).  
  
 `scriptLocation` Odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy. <xref:System.Net.WebProxy> Klasy będzie podejmować próby zlokalizowania skryptu konfiguracji (zazwyczaj nazwanego Wpad.dat) po **Użyj skryptu automatycznej konfiguracji** opcja jest zaznaczona w programie Internet Explorer.  
  
 Użyj `usesystemdefault` atrybutu dla aplikacji programu .NET Framework w wersji 1.1, które migracji do wersji 2.0.  
  
 Jeśli jest zgłaszany wyjątek `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy. <xref:System.Exception.InnerException%2A> Na wyjątku powinna mieć więcej informacji na temat przyczynę błędu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy dla lokalnych.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
