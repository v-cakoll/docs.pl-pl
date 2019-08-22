---
title: <defaultHttpCachePolicy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: 1dd31884a072d16ed004c0b49be61e8cee399787
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664153"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a>\<defaultHttpCachePolicy >, element (Ustawienia sieci)
Opisuje, czy buforowanie HTTP jest aktywne i opisuje domyślne zasady buforowania.  
  
 \<> konfiguracji  
\<system.net>  
\<requestCaching >  
\<defaultHttpCachePolicy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maximumAge`|Określa maksymalny przedział czasu, po którym obiekt w pamięci podręcznej zostanie oznaczony jako wygasły.|  
|`maximumStale`|Określa maksymalny czas poprzedzający obliczony czas Aktualności przed oznaczeniem obiektu w pamięci podręcznej jako wygasły.|  
|`minimumFresh`|Określa minimalny czas do uwzględnienia w pamięci podręcznej.|  
|`policyLevel`|Określa, czy zasady buforowania są wykonywane automatycznie, czy pamięć podręczna jest pomijana. Wartość domyślna to `BypassCache`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość `policyLevel` atrybutu `BypassCache` jest`Default`albo.  
  
 Wartości dla `maximumAge`elementów, `maximumStale`i `minimumFresh` są jawnym przedziałem czasu o formacie *d*. *HH*:*mm*:*SS* (dni, godziny, minuty i sekundy) albo stałe `minValue` lub `maxValue`, zgodnie z potrzebami.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić minimalny czas trwania sześciu godzin, maksymalny czas trwania okresu ważności wynoszący dwa dni i maksymalny czas nieodświeżony wynoszący 4 godziny.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schemat ustawień sieci](index.md)
