---
title: <defaultFtpCachePolicy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 7ff44f0251936d51b4e396c37c53322efa110227
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659421"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy >, element (Ustawienia sieci)
Opisuje, czy buforowanie FTP jest aktywne i opisuje domyślne zasady buforowania.  
  
 \<> konfiguracji  
\<system.net>  
\<requestCaching >  
\<defaultFtpCachePolicy>  
  
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
|`policyLevel`|Określa zasady buforowania FTP. Wartość domyślna to `Default`.|  
  
## <a name="policylevel-attribute"></a>policyLevel — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`Default`|Zwraca buforowany zasób, jeśli zasób jest świeży, długość zawartości jest dokładna i atrybuty daty wygaśnięcia, modyfikacji i długości zawartości są obecne.|  
|`BypassCache`|Zwraca zasób z serwera.|  
|`CacheOnly`|Zwraca buforowany zasób, jeśli długość zawartości jest obecna i jest zgodna z rozmiarem wpisu.|  
|`CacheIfAvailable`|Zwraca buforowany zasób, jeśli długość zawartości jest podana i jest zgodna z rozmiarem wpisu; w przeciwnym razie zasób jest pobierany z serwera i zwracany do obiektu wywołującego.|  
|`Revalidate`|Zwraca buforowany zasób, jeśli sygnatura czasowa zasobu w pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, zapisany w pamięci podręcznej i zwrócony do obiektu wywołującego.|  
|`Reload`|Pobiera zasób z serwera, zapisuje go w pamięci podręcznej i zwraca zasób do obiektu wywołującego.|  
|`NoCacheNoStore`|Jeśli istnieje zasób w pamięci podręcznej, zostanie on usunięty. Zasób jest pobierany z serwera i zwracany do obiektu wywołującego.|  
|`Revalidate`|Program spełnia żądanie przy użyciu buforowanej kopii zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, który jest przedstawiony dla obiektu wywołującego i zapisany w pamięci podręcznej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić zasady `NoCacheNoStore`buforowania FTP.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schemat ustawień sieci](index.md)
