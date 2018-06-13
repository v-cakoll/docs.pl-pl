---
title: '&lt;bypasslist —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d2076ee5e95ab722fe828ee625392671a6281c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743904"
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;bypasslist —&gt; — Element (ustawienia sieciowe)
Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy — >  
\<bypasslist — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Dodaje adres IP lub nazwa DNS do Lista obejść serwerów proxy.|  
|[Wyczyść](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Czyści listę obejścia.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Usuwa adres IP lub nazwa DNS lista obejść serwerów proxy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy —](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).|  
  
## <a name="remarks"></a>Uwagi  
 Lista obejść zawiera wyrażenia regularne, które opisują identyfikatorów URI który <xref:System.Net.WebRequest> wystąpień dostęp bezpośrednio zamiast z za pośrednictwem serwera proxy.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z] +\\.contoso\\.com" dopasowań żadnego hosta w domenie contoso.com, ale również zgodna każdego hosta w domenie contoso.com.cpandl.com. Aby dopasować tylko na hoście w domenie contoso.com, użyj elementu zakotwiczenia ("$"): "[a-z] +\\.contoso\\.com$".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W następującym przykładzie dodano dwa adresy do obejścia listy. Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerom rozpocząć których adresy IP 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
