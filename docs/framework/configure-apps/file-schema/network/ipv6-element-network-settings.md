---
title: <ipv6>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664099"
---
# <a name="ipv6-element-network-settings"></a>\<> IPv6, element (Ustawienia sieci)
Włącza odpowiedzi protokołu internetowego w wersji 6 (IPv6) od przestarzałych elementów <xref:System.Net.Dns> członkowskich klasy.  
  
 \<> konfiguracji  
\<system.net>  
\<settings>  
\<> IPv6  
  
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
|`enabled`|Określa, czy elementy członkowskie <xref:System.Net.Dns> klasy zwracają adresy protokołu internetowego w wersji 6 (IPv6). Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 To ustawienie umożliwia obsługę protokołu IPv6 dla przestarzałych elementów członkowskich <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Net.Dns.GetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A>,,, i <xref:System.Net.Dns.Resolve%2A>. W przypadku innych elementów członkowskich <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw adresy IPv6 mogą być zwracane, jeśli w systemie operacyjnym jest włączony protokół IPv6.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć obsługę protokołu IPv6 dla <xref:System.Net.Dns> klasy.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
