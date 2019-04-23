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
ms.openlocfilehash: 904c8e23f7a09a975a6f3b9322ed6bc4148d9ba4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098289"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<Dodaj >, Element dla bypasslist (ustawienia sieci)
Dodaje adres IP lub nazwę DNS do listy pomijania proxy.  
  
 \<Konfiguracja >  
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
|**address**|Wyrażenie regularne, zawierająca opis, adres IP lub nazwę DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 `add` Wstawia element wyrażeń regularnych, opisujący adresy IP lub nazwy serwera DNS do listy adresów, które pomijają serwer proxy.  
  
 Wartość `address` atrybut powinien być wyrażenie regularne, które opisuje zestaw adresów IP lub nazw hostów.  
  
 Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu. Wyrażenie regularne "[a-z] +\\.contoso\\.com" dopasowań dowolnego hosta w domenie contoso.com, ale również pasuje do dowolnego hosta w domenie contoso.com.cpandl.com. Aby dopasować tylko na hoście w domenie contoso.com, użyj elementu zakotwiczenia ("$"): "[a-z] +\\.contoso\\.com$".  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje dwa adresy do listy pomijania. Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerom rozpoczyna się których adresy IP 192.168.  
  
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
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
