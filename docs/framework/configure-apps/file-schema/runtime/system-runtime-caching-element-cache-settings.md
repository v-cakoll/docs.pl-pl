---
title: "&lt;System.Runtime.Caching —&gt; — Element (ustawienia pamięci podręcznej)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83964d3a6e07267eaa946fa306301bc6d0d16e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a>&lt;System.Runtime.Caching —&gt; — Element (ustawienia pamięci podręcznej)
Zapewnia konfigurację domyślną w pamięci <xref:System.Runtime.Caching.ObjectCache> wykonywania za pośrednictwem `memoryCache` wpis w pliku konfiguracji.  
  
 \<Konfiguracja >  
\<System.Runtime.Caching — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 `None`  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<memoryCache >](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasy w tej przestrzeni nazw umożliwiają używanie buforowania obiektów, podobnie jak w programie ASP.NET, ale bez zależności w `System.Web` zestawu. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Dane wyjściowe pamięci podręcznej funkcji i typów w <xref:System.Runtime.Caching> przestrzeni nazw są nowością w programie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób skonfigurować pamięć podręczną, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy. W przykładzie pokazano sposób konfigurowania wystąpienia `namedCaches` wpis pamięci podręcznej. Nazwa pamięci podręcznej ma ustawioną domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu "default".  
  
 `cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu zostaną ustawione na zero. Ustawienia te atrybuty zero oznacza <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru. Implementacja pamięci podręcznej należy porównać bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<memoryCache > elementu (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
