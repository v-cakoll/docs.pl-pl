---
title: <memoryCache>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153987"
---
# <a name="memorycache-element-cache-settings"></a>\<MemoryCache> Element (ustawienia pamięci podręcznej)
Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie. Klasa <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> definiuje [memoryCache](memorycache-element-cache-settings.md) element, który służy do konfigurowania pamięci podręcznej. Wiele wystąpień <xref:System.Runtime.Caching.MemoryCache> klasy może służyć w jednej aplikacji. Każdy `memoryCache` element w pliku konfiguracji może <xref:System.Runtime.Caching.MemoryCache> zawierać ustawienia dla nazwanego wystąpienia.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>memoryCache**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.Runtime.Caching.MemoryCache>Klasa.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maksymalny rozmiar pamięci w megabajtach, <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie obiektu. Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że heurystyka autosize klasy jest używana domyślnie.|  
|`Name`|Nazwa konfiguracji pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Procent pamięci fizycznej, która może być używana przez pamięć podręczną. Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że heurystyka autosize klasy jest używana domyślnie.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Wartość jest wprowadzana w formacie "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nazwaneCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji `namedCache` dla wystąpienia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracyjne](../configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
|[\<>system.runtime.caching](system-runtime-caching-element-cache-settings.md)|Zawiera typy, które umożliwiają implementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w program .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa <xref:System.Runtime.Caching.MemoryCache> jest konkretną implementacją <xref:System.Runtime.Caching.ObjectCache> klasy abstrakcyjnej. Wystąpienia <xref:System.Runtime.Caching.MemoryCache> klasy mogą być dostarczane z informacjami o konfiguracji z plików konfiguracyjnych aplikacji. Sekcja konfiguracji [memoryCache](memorycache-element-cache-settings.md) `namedCaches` zawiera kolekcję konfiguracji.  
  
 Po zainicjowaniu obiektu pamięci podręcznej, najpierw próbuje `namedCaches` znaleźć wpis, który pasuje do nazwy w parametrze, który jest przekazywany do konstruktora pamięci podręcznej. Jeśli `namedCaches` zostanie znaleziony wpis, informacje o sondowaniu i zarządzaniu pamięcią są pobierane z pliku konfiguracji.  
  
 Proces inicjowania następnie określa, czy wszystkie wpisy konfiguracji zostały zastąpione przy użyciu opcjonalnej kolekcji par nazw/wartości informacji o konfiguracji w konstruktorze. Jeśli przekażesz jedną z następujących wartości w kolekcji pary nazwa/wartość, te wartości zastępują informacje uzyskane z pliku konfiguracji:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, <xref:System.Runtime.Caching.MemoryCache> jak ustawić nazwę obiektu na `name` domyślną nazwę obiektu pamięci podręcznej, ustawiając atrybut na "Domyślny".  
  
 Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryLimitPercentage` atrybut są ustawione na zero. Ustawienie tych atrybutów na <xref:System.Runtime.Caching.MemoryCache> zero oznacza, że heurystyka automatycznego szesnasty są używane domyślnie. Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci z bezwzględnych i procentowych limitów pamięci co dwie minuty.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Caching.MemoryCache>
- [\<element> system.runtime.caching (ustawienia pamięci podręcznej)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches> Element (Ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
