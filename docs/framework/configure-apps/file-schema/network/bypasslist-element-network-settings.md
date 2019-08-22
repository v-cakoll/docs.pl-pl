---
title: <bypasslist>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 10d2a025096579c6bed64f82cc955deb0542717c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664204"
---
# <a name="bypasslist-element-network-settings"></a>\<BypassList >, element (Ustawienia sieci)
Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.  
  
 \<> konfiguracji  
\<system.net>  
\<defaultProxy>  
\<bypasslist>  
  
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
|[add](add-element-for-bypasslist-network-settings.md)|Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.|  
|[Wyczyść](clear-element-for-bypasslist-network-settings.md)|Czyści listę pomijania.|  
|[remove](remove-element-for-bypasslist-network-settings.md)|Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Uwagi  
 Lista obejścia zawiera wyrażenia regularne, które opisują <xref:System.Net.WebRequest> identyfikatory URI, które uzyskują dostęp bezpośrednio, zamiast za pomocą serwera proxy.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z] +\\. contoso\\. com" dopasowuje dowolny host w domenie contoso.com, ale również jest zgodny z dowolnym hostem w domenie contoso.com.cpandl.com. Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] +\\. contoso\\. com $".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje dwa adresy do listy pomijania. Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adresy IP zaczynają się od 192,168.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
