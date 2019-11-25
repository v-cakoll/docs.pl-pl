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
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283093"
---
# <a name="performancecounter-element-network-settings"></a>\<element > performanceCounter (Ustawienia sieci)
Włącza lub wyłącza liczniki wydajności sieci.  

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<liczniki wydajności >**

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
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.|  
  
## <a name="remarks"></a>Uwagi  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany. Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji. Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci. Aby uzyskać więcej informacji na temat określonych liczników wydajności sieci, zobacz [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).  
  
 Wartością domyślną jest to, że liczniki wydajności sieci są wyłączone.  
  
 Właściwość <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> może służyć do uzyskiwania bieżącej wartości **włączonego** atrybutu z odpowiednich plików konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować <xref:System.Net> i powiązane przestrzenie nazw w celu włączenia liczników wydajności sieci.  
  
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
- [Liczniki wydajności sieci](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
