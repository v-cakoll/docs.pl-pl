---
title: "&lt;requestCaching —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2737e67fe1fe1e33b2600f448b02321f6ce1888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching —&gt; — Element (ustawienia sieciowe)
Określa mechanizm buforowania żądań sieciowych.  
  
 \<Konfiguracja >  
\<System.NET >  
\<requestCaching — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`isPrivateCache`|Określa, czy pamięć podręczna zapewnia izolację między informacjami zawartymi w różnych użytkowników. Wartość domyślna to `true`. Ta wartość powinna być `false` dla aplikacji warstwy środkowej.|  
|`disableAllCaching`|Określa, czy buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie można zastąpić programowo.|  
|`defaultPolicyLevel`|Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia. Wartość domyślna to `BypassCache`.|  
|`unspecifiedMaximumAge`|Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.|  
  
## <a name="policylevel-attribute"></a>PolicyLevel, który atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`Default`|Zwraca buforowane zasobu, jeśli zasób jest nowa, długość zawartości jest dokładna i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.|  
|`BypassCache`|Zwraca zasobu z serwera.|  
|`CacheOnly`|Zwraca buforowane zasobu, jeśli długość zawartości jest obecny i dopasowuje rozmiar wpisu.|  
|`CacheIfAvailable`|Zwraca buforowane zasobów, jeśli zostanie podana długość zawartości dopasowuje rozmiar wpisu; w przeciwnym razie zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Zwraca buforowane zasobu, jeśli sygnatury czasowej buforowanych zasobów jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.|  
|`Reload`|Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.|  
|`NoCacheNoStore`|Jeśli istnieje zasób pamięci podręcznej, jest ono usunięte. Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Spełnia żądania przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatury czasowej jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przedstawione do obiektu wywołującego i są przechowywane w pamięci podręcznej,|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[defaulthttpcachepolicy —](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie HTTP jest aktywna i opisano domyślne zasad buforowania.|  
|[\<defaultftpcachepolicy — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie FTP jest aktywna i opisano domyślne zasad buforowania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wyłączania buforowaniu.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
