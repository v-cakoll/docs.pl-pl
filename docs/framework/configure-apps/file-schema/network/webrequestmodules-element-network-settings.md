---
title: <webRequestModules>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: c30a7a0bcce62c99d7c1ec0ff17389b8c2cd2f17
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663943"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules >, element (Ustawienia sieci)
Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.  
  
 \<> konfiguracji  
\<system.net>  
\<webRequestModules>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|Dodaje niestandardowy moduł żądania sieci Web do aplikacji.|  
|[Wyczyść](clear-element-for-webrequestmodules-network-settings.md)|Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|Usuwa niestandardowy moduł żądania sieci Web z aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 Element rejestruje elementy podrzędne <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów sieciowych. `webRequestModules` Moduły żądania sieci Web muszą implementować <xref:System.Net.IWebRequestCreate> interfejs.  
  
 .NET Framework obejmuje moduły żądania sieci Web dla identyfikatorów URI zaczynających `http://`się `https://`od, `file://`i. Moduły domyślne można zastąpić tylko przez zarejestrowanie modułu niestandardowego w pliku konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje domyślny moduł HTTP. Należy zastąpić wartości wersji i PublicKeyToken wartościami prawidłowymi dla określonego modułu.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Schemat ustawień sieci](index.md)
