---
title: '&lt;namedCaches&gt; — Element (ustawienia pamięci podręcznej)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a74dfaf883ea23514c6bc4641d9d576f5baf10b4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206310"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; — Element (ustawienia pamięci podręcznej)
Określa kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Właściwości odwołuje się zestaw ustawień konfiguracji z co najmniej jeden `namedCaches` elementy pliku konfiguracji.  
  
 \<Konfiguracja >  
\< System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Wartość całkowitą, która określa maksymalny dozwolony rozmiar w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> może zwiększyć się. Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.|  
|`name`|Nazwa pamięci podręcznej.|  
|`physicalMemoryLimitPercentage`|Wartość całkowitą pomiędzy 0 a 100 określającą maksymalną wartość procentową fizycznie zainstalowanym komputerze pamięci, które mogą być używane przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.|  
|`pollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci limitów bezwzględne i opartych na procentach pamięci, które są ustawione na wystąpienie pamięci podręcznej. Ta wartość jest wprowadzana w formacie "Gg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Dodaje nazwaną pamięć podręczną do `namedCaches` kolekcji w pamięci podręcznej.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Czyści `namedCaches` kolekcji w pamięci podręcznej.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Usuwa wpis nazwaną pamięć podręczną z `namedCaches` kolekcji w pamięci podręcznej.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Sekcja konfiguracji pamięci podręcznej pamięci w pliku Web.config może zawierać `add`, `remove`, i `clear` atrybuty dla `namedCaches` kolekcji. Każdy `namedCaches` wpis jest unikatowo identyfikowana przez `name` atrybutu.  
  
 Odwoływanie się do informacji w plikach konfiguracji aplikacji można pobrać wystąpień wpisy w pamięci podręcznej pamięci. Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracji. Domyślne wystąpienie pamięci podręcznej jest wystąpieniem, który jest zwracany z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.  
  
 Jeśli ustawiono atrybut name "domyślne", element używa domyślnego wystąpienia pamięci podręcznej pamięci.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić nazwę pamięci podręcznej domyślną nazwę wpisu pamięci podręcznej, ustawiając `name` atrybutu "default".  
  
 `cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu jest równa zero. Ustawienia te atrybuty zero oznacza, że Algorytm heurystyczny automatyczne określanie rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane. Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.  
  
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
 [\<memoryCache >, Element (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
