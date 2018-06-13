---
title: '&lt;Dodaj&gt; elementu &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743826"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;Dodaj&gt; elementu &lt;namedCaches&gt;
Dodaje `namedCache` wpisu `namedCaches` kolekcji dla pamięci podręcznej.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach) który wystąpienia <xref:System.Runtime.Caching.MemoryCache> odpowiednio do. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru klasy.|  
|`Name`|Nazwa pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Wartość całkowitą pomiędzy 0 a 100 określająca maksymalny procent pamięci fizycznie zainstalowanym komputerze, który może być zużyte przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczna zmiana rozmiaru klasy.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "Gg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 `None`  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 `add` Element dodaje wpis do `namedCaches` kolekcji dla pamięci podręcznej. Można użyć [wyczyść](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element przed użyciem `add` elementu, aby mieć pewność, że nie ma żadnych innych o nazwie pamięci podręcznych w kolekcji. Ten element może być użyty w pliku machine.config i w pliku Web.config.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zdefiniować ustawienia domyślne `namedCache` wpisu `namedCaches` kolekcji dla pamięci podręcznej.  
  
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
 [\<namedCaches > elementu (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
