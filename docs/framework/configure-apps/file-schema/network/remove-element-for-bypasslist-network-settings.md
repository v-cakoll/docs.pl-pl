---
title: '&lt;Usuń&gt; , Element dla bypasslist (ustawienia sieci)'
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
ms.openlocfilehash: 83449aa2df2b0442f5ba5e1f152232b007bcdc15
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193711"
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a>&lt;Usuń&gt; , Element dla bypasslist (ustawienia sieci)
Usuwa adres IP lub nazwa DNS z listy obejścia serwera proxy.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy — >  
\<bypasslist >  
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
|`address`|Wyrażenie regularne, zawierająca opis, adres IP lub nazwę DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Elementu usuwa wyrażeń regularnych, opisujący adresy IP lub nazwy serwera DNS z listy adresów, które pomijają serwer proxy. Adresy zostały zdefiniowane wcześniej w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.  
  
 Wartość `address` atrybut powinien być wyrażenie regularne, które opisuje zestaw adresów IP lub nazw hostów.  
  
 Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa wszelkie poprzednią definicję dla domeny adventure works.com, a następnie dodaje domeny contoso.com do listy pomijania.  
  
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
- <xref:System.Net.WebProxy?displayProperty=nameWithType>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
