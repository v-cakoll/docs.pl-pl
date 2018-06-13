---
title: '&lt;Dodaj&gt; elementu bypasslist — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d786d4fd7e6663649408b36fb518db06063ef916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754522"
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a>&lt;Dodaj&gt; elementu bypasslist — (ustawienia sieciowe)
Dodaje adres IP lub nazwa DNS do Lista obejść serwerów proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy — >  
\<bypasslist — >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|**Adres**|Wyrażenie regularne opisujące adresu IP lub nazwy DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist —](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 `add` Element wstawia wyrażeń regularnych opisujące adresy IP lub nazwy serwera DNS do listy adresów, które Obejdź serwer proxy.  
  
 Wartość `address` atrybutu powinna być wyrażenie regularne opisuje zestaw adresów IP lub nazwy hosta.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z] +\\.contoso\\.com" dopasowań żadnego hosta w domenie contoso.com, ale również zgodna każdego hosta w domenie contoso.com.cpandl.com. Aby dopasować tylko na hoście w domenie contoso.com, użyj elementu zakotwiczenia ("$"): "[a-z] +\\.contoso\\.com$".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 W następującym przykładzie dodano dwa adresy do obejścia listy. Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerów rozpoczyna którego adres IP z 192.168.  
  
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
