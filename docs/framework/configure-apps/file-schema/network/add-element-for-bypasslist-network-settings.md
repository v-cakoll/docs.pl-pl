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
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155080"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<dodaj element> dla bypasslist (Ustawienia sieciowe)
Dodaje adres IP lub nazwę DNS do listy pomijania serwera proxy.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>obwodnicy**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**  
  
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
|**Adres**|Wyrażenie regularne opisujące adres IP lub nazwę DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Bypasslist](bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie używają serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 Element `add` wstawia wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS do listy adresów, które pomijają serwer proxy.  
  
 Wartość atrybutu `address` powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z]+\\.contoso\\.com" pasuje do dowolnego hosta w domenie contoso.com, ale pasuje również do dowolnego hosta w domenie contoso.com.cpandl.com. Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z]+\\.contoso\\.com$".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz . [Wyrażenia regularne programu .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje dwa adresy do listy pomijania. Pierwszy omija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi omija serwer proxy dla wszystkich serwerów, których adres IP zaczyna się od 192.168.  
  
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

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
