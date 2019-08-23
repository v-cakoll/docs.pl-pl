---
title: <add>, element dla bypasslist (ustawienia sieci)
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
ms.openlocfilehash: da234402c6ec7e2c1f85e4bd674517b1147f0d18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927481"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<Dodaj element > dla BypassList (Ustawienia sieci)
Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.  
  
 \<> konfiguracji  
\<system.net>  
\<defaultProxy>  
\<bypasslist>  
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
|**address**|Wyrażenie regularne opisujące adres IP lub nazwę DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 `add` Element wstawia wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS do listy adresów, które pomijają serwer proxy.  
  
 Wartość `address` atrybutu powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z] +\\. contoso\\. com" dopasowuje dowolny host w domenie contoso.com, ale również jest zgodny z dowolnym hostem w domenie contoso.com.cpandl.com. Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] +\\. contoso\\. com $".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje dwa adresy do listy pomijania. Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adres IP rozpoczyna się od 192,168.  
  
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
