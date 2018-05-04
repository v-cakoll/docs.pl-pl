---
title: '&lt;memoryCache&gt; elementu (ustawienia pamięci podręcznej)'
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d0d741fd8193c7d874d70248cbd149f11163ed0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmemorycachegt-element-cache-settings"></a>&lt;memoryCache&gt; elementu (ustawienia pamięci podręcznej)
Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Klasa definiuje [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) elementu, którego można użyć do skonfigurowania pamięci podręcznej. Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasa może być używana w pojedynczej aplikacji. Każdy `memoryCache` w pliku konfiguracji może zawierać ustawienia dla nazwane <xref:System.Runtime.Caching.MemoryCache> wystąpienia.  
  
 \<Konfiguracja >  
\<system.runtime.caching>  
\<memoryCache>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.Runtime.Caching.MemoryCache> Klasa.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maksymalny rozmiar pamięci, wyrażony w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektu odpowiednio do. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize klasy.|  
|`Name`|Nazwa konfiguracji pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Procent pamięci fizycznej używanej przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize klasy.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Wartość jest wprowadzana w formacie "Gg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji `namedCache` wystąpienia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Zawiera typy, które pozwalają na wdrożenie buforowanie danych wyjściowych w aplikacjach, które są wbudowane w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Runtime.Caching.MemoryCache> Konkretną implementację klasy abstrakcyjnej jest klasa <xref:System.Runtime.Caching.ObjectCache> klasy. Wystąpienia <xref:System.Runtime.Caching.MemoryCache> klasy można podać informacje o konfiguracji z pliki konfiguracji aplikacji. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) sekcja konfiguracji zawiera `namedCaches` konfiguracji kolekcji.  
  
 Po zainicjowaniu obiektu oparty na pamięci podręcznej po raz pierwszy próbuje odnaleźć `namedCaches` wpis, który odpowiada nazwie w parametr, który jest przekazywany do konstruktora pamięci podręcznej pamięci. Jeśli `namedCaches` można odnaleźć wpisu, sondowania i informacji o zarządzaniu pamięci są pobierane z pliku konfiguracji.  
  
 Proces inicjowania Określa, czy wszystkie pozycje konfiguracji zostały zastąpione, za pomocą opcjonalnych kolekcja par nazwa/wartość informacji o konfiguracji w konstruktorze. Jeśli jeden z następujących wartości przekazywane w kolekcji par nazwa/wartość, te wartości zastąpić informacjami uzyskanymi z pliku konfiguracji:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiekt do domyślnej nazwy obiektu pamięci podręcznej przez ustawienie `name` atrybutu "default".  
  
 `cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryLimitPercentage` atrybutu zostaną ustawione na zero. Ustawienia te atrybuty zero oznacza <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru. Implementacja pamięci podręcznej należy porównać bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Caching.MemoryCache>  
 [\<system.runtime.caching> Element (Cache Settings)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<namedCaches > elementu (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
