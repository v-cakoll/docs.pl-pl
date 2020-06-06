---
title: <requestCaching>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: afee69eb894518b1c88483e34a1d64d452019244
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802127"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching>, element (ustawienia sieci)
Kontroluje mechanizm buforowania dla żądań sieci.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`isPrivateCache`|Określa, czy pamięć podręczna zapewnia izolację między informacjami różnych użytkowników. Wartość domyślna to `true`. Ta wartość powinna być `false` dla aplikacji warstwy środkowej.|  
|`disableAllCaching`|Określa, że buforowanie jest wyłączone dla wszystkich odpowiedzi sieci Web i nie może zostać przesłonięte programowo.|  
|`defaultPolicyLevel`|Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczeniu. Wartość domyślna to `BypassCache`.|  
|`unspecifiedMaximumAge`|Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.|  
  
## <a name="policylevel-attribute"></a>policyLevel — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`Default`|Zwraca buforowany zasób, jeśli zasób jest świeży, długość zawartości jest dokładna i atrybuty daty wygaśnięcia, modyfikacji i długości zawartości są obecne.|  
|`BypassCache`|Zwraca zasób z serwera.|  
|`CacheOnly`|Zwraca buforowany zasób, jeśli długość zawartości jest obecna i jest zgodna z rozmiarem wpisu.|  
|`CacheIfAvailable`|Zwraca buforowany zasób, jeśli długość zawartości jest podana i jest zgodna z rozmiarem wpisu; w przeciwnym razie zasób jest pobierany z serwera i zwracany do obiektu wywołującego.|  
|`Revalidate`|Zwraca buforowany zasób, jeśli sygnatura czasowa zasobu w pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierany z serwera, przechowywany w pamięci podręcznej i zwracany do obiektu wywołującego.|  
|`Reload`|Pobiera zasób z serwera, zapisuje go w pamięci podręcznej i zwraca zasób do obiektu wywołującego.|  
|`NoCacheNoStore`|Jeśli istnieje zasób w pamięci podręcznej, zostanie on usunięty. Zasób jest pobierany z serwera i zwracany do obiektu wywołującego.|  
|`Revalidate`|Program spełnia żądanie przy użyciu buforowanej kopii zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, który jest prezentowany obiektowi wywołującemu, i jest przechowywany w pamięci podręcznej,|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie HTTP jest aktywne i opisuje domyślne zasady buforowania.|  
|[\<defaultFtpCachePolicy>— Element (Ustawienia sieci)](defaultftpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie FTP jest aktywne i opisuje domyślne zasady buforowania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć wszystkie buforowanie.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
