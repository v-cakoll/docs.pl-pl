---
title: '&lt;IPv6&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4b73e5d781829292513e809c39ac9de9dfc6d0e8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742487"
---
# <a name="ltipv6gt-element-network-settings"></a>&lt;IPv6&gt; elementu (ustawienia sieciowe)
Internet Protocol w wersji 6 (IPv6) umożliwia odpowiedzi z przestarzałych elementów członkowskich <xref:System.Net.Dns> klasy.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
\<IPv6 >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`enabled`|Określa, czy elementy członkowskie <xref:System.Net.Dns> klasy zwracać Internet Protocol w wersji 6 (IPv6) adresów. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 To ustawienie włącza obsługi protokołu IPv6 dla członków przestarzałe <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, i <xref:System.Net.Dns.Resolve%2A>. Dla innych członków <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw, adresy IPv6 mogą być zwracane w przypadku protokołu IPv6 jest włączona w systemie operacyjnym.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób włączania obsługi protokołu IPv6 dla <xref:System.Net.Dns> klasy.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
