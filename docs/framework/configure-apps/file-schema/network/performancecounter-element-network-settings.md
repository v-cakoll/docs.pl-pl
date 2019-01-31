---
title: <performanceCounter> — Element (Ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4603a942788d31a049196fb699d07a13551fa443
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279763"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter >, Element (ustawienia sieci)
Włącza lub wyłącza liczniki wydajności funkcji sieciowych.  
  
 \<Konfiguracja >  
\<system.net>  
\<settings>  
\<performanceCounters>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Określa, czy są włączone liczniki wydajności funkcji sieciowych. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia. Wszystkie liczniki wydajności funkcji sieciowych są włączone lub wyłączone przy użyciu pojedynczego ustawienia w pliku konfiguracji. Poszczególne liczniki wydajności funkcji sieciowych nie może być włączona lub wyłączona. Aby uzyskać więcej informacji na temat określonych liczniki wydajności funkcji sieciowych, zobacz [liczniki wydajności funkcji sieciowych](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).  
  
 Wartość domyślna to tego wydajność sieci, które liczniki są wyłączone.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości **włączone** atrybut z właściwych plików konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net> i pokrewnych przestrzeniach nazw, aby włączyć liczniki wydajności funkcji sieciowych.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [Liczniki wydajności funkcji sieciowych](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
