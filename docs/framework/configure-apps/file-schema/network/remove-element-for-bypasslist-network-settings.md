---
title: '&lt;Usuń&gt; elementu bypasslist — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5c7918048743d53d8523ec399d1a11c67152a2bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742952"
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a>&lt;Usuń&gt; elementu bypasslist — (ustawienia sieciowe)
Usuwa adres IP lub nazwa DNS lista obejść serwerów proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy — >  
\<bypasslist — >  
\<Usuń >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`address`|Wyrażenie regularne opisujące adresu IP lub nazwy DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist —](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Wyrażeń regularnych opisujące adresy IP lub nazwy serwera DNS z listy adresów, które Obejdź serwer proxy usuwa element. Adresy zostały zdefiniowane wcześniej w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.  
  
 Wartość `address` atrybutu powinna być wyrażenie regularne opisuje zestaw adresów IP lub nazwy hosta.  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa wszelkie poprzednie definicji dla domeny firmy adventure works.com, a następnie dodanie domeny contoso.com, do listy obejścia.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
