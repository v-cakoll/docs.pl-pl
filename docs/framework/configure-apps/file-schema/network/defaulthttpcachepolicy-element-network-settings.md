---
title: "&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2db2fd10ca20209c21c8add71d8ee4f26951ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a>&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieciowe)
Opisuje, czy buforowanie HTTP jest aktywna i opisano domyślne zasad buforowania.  
  
 \<Konfiguracja >  
\<System.NET >  
\<requestCaching — >  
\<defaulthttpcachepolicy — >  
  
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
|`maximumAge`|Określa maksymalny czas, przed obiektu w pamięci podręcznej jest oznaczona jako wygasła.|  
|`maximumStale`|Określa maksymalny czas późniejsza niż godzina świeżości obliczaną przed obiektu w pamięci podręcznej jest oznaczona jako wygasła.|  
|`minimumFresh`|Określa minimalny czas wziąć pod uwagę nowego obiektu w pamięci podręcznej.|  
|`policyLevel`|Określa, czy zasad buforowania odbywa się automatycznie, czy pomijana jest pamięć podręczna. Wartość domyślna to `BypassCache`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[requestCaching —](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Określa mechanizm buforowania żądań sieciowych.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość `policyLevel` jest atrybut `BypassCache` lub `Default`.  
  
 Wartości `maximumAge`, `maximumStale`, i `minimumFresh` elementy są albo jawne interwał w formacie *d*. *hh*:*mm*:*ss* (dni, godziny, minuty i sekundy), lub stałe `minValue` lub `maxValue`, gdzie to właściwe.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić minimalny czas świeże sześć godzin przez czas maksymalny wiek dwa dni, a maksymalny czas starych czterech godzin.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
