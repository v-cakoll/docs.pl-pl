---
title: <performanceCounter>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 05aac6c1ed3c04bce263a45cafdb9bec906bd75b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664061"
---
# <a name="performancecounter-element-network-settings"></a>\<performanceCounter >, element (Ustawienia sieci)
Włącza lub wyłącza liczniki wydajności sieci.  
  
 \<> konfiguracji  
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
|`enabled`|Określa, czy są włączone liczniki wydajności sieci. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany. Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji. Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci. Aby uzyskać więcej informacji na temat określonych liczników wydajności sieci, zobacz [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).  
  
 Wartością domyślną jest to, że liczniki wydajności sieci są wyłączone.  
  
 Właściwość może służyć do uzyskiwania bieżącej wartości włączonego atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, <xref:System.Net> jak skonfigurować i powiązane przestrzenie nazw w celu włączenia liczników wydajności sieci.  
  
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
- [Schemat ustawień sieci](index.md)
- [Liczniki wydajności sieci](../../../debug-trace-profile/performance-counters.md#networking)
