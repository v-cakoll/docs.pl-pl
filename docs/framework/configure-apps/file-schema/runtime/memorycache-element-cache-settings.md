---
title: <memoryCache> Element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: dbb46e7cf2580635add9d3100c8177c99cbae6bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126818"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache >, Element (ustawienia pamięci podręcznej)
Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Klasa definiuje [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element, który służy do konfigurowania pamięci podręcznej. Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy mogą być używane w jednej aplikacji. Każdy `memoryCache` elementu w pliku konfiguracji mogą zawierać ustawienia dla nazwane <xref:System.Runtime.Caching.MemoryCache> wystąpienia.  
  
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
|`CacheMemoryLimitMegabytes`|Maksymalny rozmiar pamięci, w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektów może zwiększyć się. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize tej klasy.|  
|`Name`|Nazwa konfiguracji pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Procent pamięci fizycznej używanej przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne autosize tej klasy.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej. Wartość jest wprowadzana w formacie "Gg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji `namedCache` wystąpienia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Zawiera typy, które pozwalają na implementowanie buforowania danych wyjściowych w aplikacjach, które są wbudowane w [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Runtime.Caching.MemoryCache> Klasa jest konkretną implementację abstrakcyjnej <xref:System.Runtime.Caching.ObjectCache> klasy. Wystąpienia elementu <xref:System.Runtime.Caching.MemoryCache> klasy mogą być dostarczane za pomocą informacji o konfiguracji z plików konfiguracji aplikacji. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) sekcja konfiguracji zawiera `namedCaches` konfiguracyjnych.  
  
 Po zainicjowaniu obiektu pamięci podręcznej na podstawie pamięci najpierw podejmie próbę odnalezienia `namedCaches` wpis, który jest zgodna z nazwą parametru, który jest przekazywany do konstruktora pamięci podręcznej pamięci. Jeśli `namedCaches` znajduje się wpis, sondowania i informacje o zarządzaniu pamięci są pobierane z pliku konfiguracji.  
  
 Proces inicjowania Określa, czy wszystkie wpisy konfiguracji zostały zastąpione, za pomocą opcjonalnych kolekcję par nazwa/wartość informacji o konfiguracji w konstruktorze. Jeśli jeden z następujących wartości są przekazywane w kolekcji par nazwa/wartość, te wartości zastąpić informacjami uzyskanymi z pliku konfiguracji:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiekt do domyślnej nazwy obiektu pamięci podręcznej, ustawiając `name` atrybutu "default".  
  
 `cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryLimitPercentage` atrybutu jest równa zero. Ustawienia te atrybuty zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru. Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Caching.MemoryCache>
- [\<System.Runtime.Caching >, Element (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [\<namedCaches >, Element (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
