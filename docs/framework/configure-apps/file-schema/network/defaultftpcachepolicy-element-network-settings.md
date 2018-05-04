---
title: '&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e4ea16c925114d4ad4054af5f340c764ed6fe4fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieciowe)
Opisuje, czy buforowanie FTP jest aktywna i opisano domyślne zasad buforowania.  
  
 \<Konfiguracja >  
\<system.net>  
\<requestCaching — >  
\<defaultftpcachepolicy — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`policyLevel`|Określa FTP zasad buforowania. Wartość domyślna to `Default`.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel, który atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`Default`|Zwraca buforowane zasobu, jeśli zasób jest nowa, długość zawartości jest dokładna i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.|  
|`BypassCache`|Zwraca zasobu z serwera.|  
|`CacheOnly`|Zwraca buforowane zasobu, jeśli długość zawartości jest obecny i dopasowuje rozmiar wpisu.|  
|`CacheIfAvailable`|Zwraca buforowane zasobów, jeśli zostanie podana długość zawartości dopasowuje rozmiar wpisu; w przeciwnym razie zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Zwraca buforowane zasobu, jeśli sygnatury czasowej buforowanych zasobów jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie wartość zasób jest pobierany z serwera, przechowywane w pamięci podręcznej i zwracany do obiektu wywołującego.|  
|`Reload`|Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.|  
|`NoCacheNoStore`|Jeśli istnieje zasób pamięci podręcznej, jest ono usunięte. Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Spełnia żądania przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatury czasowej jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobrane z serwera, przedstawione do obiektu wywołującego i przechowywane w pamięci podręcznej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[requestCaching —](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Określa mechanizm buforowania żądań sieciowych.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić FTP buforowanie zasady `NoCacheNoStore`.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
