---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663618"
---
# <a name="memorycache-element-cache-settings"></a>\<Elemencie MemoryCache >, element (ustawienia pamięci podręcznej)
Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie. Klasa definiuje element elemencie MemoryCache, którego można użyć do skonfigurowania pamięci podręcznej. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy może być używanych w pojedynczej aplikacji. Każdy `memoryCache` element w pliku konfiguracji może zawierać ustawienia dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpienia.  
  
 \<> konfiguracji  
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
 <xref:System.Runtime.Caching.MemoryCache>określonej.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maksymalny rozmiar pamięci (w megabajtach), w którym można zwiększyć wystąpienie <xref:System.Runtime.Caching.MemoryCache> obiektu. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.|  
|`Name`|Nazwa konfiguracji pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Wartość procentowa pamięci fizycznej, która może być używana przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autodopasowywania rozmiaru klasy są używane domyślnie.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej. Wartość jest wprowadzana w formacie "gg: MM: SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji dla tego `namedCache` wystąpienia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest konkretną implementacją klasy abstrakcyjnej <xref:System.Runtime.Caching.ObjectCache>. <xref:System.Runtime.Caching.MemoryCache> <xref:System.Runtime.Caching.MemoryCache> Wystąpienia klasy mogą być dostarczane z informacjami o konfiguracji z plików konfiguracji aplikacji. Sekcja konfiguracja [elemencie MemoryCache](memorycache-element-cache-settings.md) zawiera `namedCaches` kolekcję konfiguracji.  
  
 Gdy obiekt pamięci podręcznej oparty na pamięci jest inicjowany, najpierw próbuje `namedCaches` znaleźć wpis pasujący do nazwy w parametrze, który jest przesyłany do konstruktora pamięci podręcznej. W przypadku znalezienia wpisu informacje dotyczące sondowania i zarządzania pamięci są pobierane z pliku konfiguracyjnego. `namedCaches`  
  
 Następnie proces inicjowania określa, czy wszystkie wpisy konfiguracji zostały zastąpione, przy użyciu opcjonalnej kolekcji par nazwa/wartość informacji o konfiguracji w konstruktorze. W przypadku przekazania jednej z następujących wartości w kolekcji nazwa/wartość te wartości zastępują informacje uzyskane z pliku konfiguracji:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić nazwę <xref:System.Runtime.Caching.MemoryCache> obiektu na domyślną nazwę obiektu pamięci podręcznej przez `name` ustawienie atrybutu na wartość "domyślny".  
  
 `cacheMemoryLimitMegabytes` Atrybut`physicalMemoryLimitPercentage` i atrybut są ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie. Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
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
- [\<system.runtime.caching> Element (Cache Settings)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches >, element (ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
