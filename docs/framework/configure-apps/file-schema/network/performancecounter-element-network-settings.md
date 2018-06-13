---
title: '&lt;performanceCounter&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5879614fd34fe645899f1b95f41e9b0675418292
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742640"
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt; elementu (ustawienia sieciowe)
Włącza lub wyłącza liczniki wydajności sieci.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
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
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia. Wszystkie sieci liczniki wydajności są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji. Poszczególne sieci liczniki wydajności nie może być włączona lub wyłączona. Aby uzyskać więcej informacji na określonej sieci liczniki wydajności, zobacz [sieci liczniki wydajności](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).  
  
 Wartość domyślna to, że wydajność sieci, które liczniki są wyłączone.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego **włączone** atrybutu z plików zastosowania konfiguracji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net> i związanych z przestrzeni nazw, aby włączyć liczniki wydajności sieci.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [Liczniki wydajności sieci](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
