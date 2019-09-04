---
title: <add>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252890"
---
# <a name="add-element-for-namedcaches"></a>\<add> Element for \<namedCaches>
`namedCache` Dodaje wpis`namedCaches` do kolekcji dla pamięci podręcznej pamięci.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. Runtime. buforowanie >** ](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Elemencie MemoryCache >** ](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
    <add name="Default" />  
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
|`CacheMemoryLimitMegabytes`|Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach), do którego wystąpienie <xref:System.Runtime.Caching.MemoryCache> może się rozwijać. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autowymiarowania klasy są używane domyślnie.|  
|`Name`|Nazwa pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Wartość całkowita z zakresu od 0 do 100, która określa maksymalną wartość procentową fizycznie zainstalowanej pamięci komputera, która może być używana przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autowymiarowania klasy są używane domyślnie.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "gg: MM: SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 `None`  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 Element dodaje wpis `namedCaches` do kolekcji dla pamięci podręcznej pamięci. `add` Można użyć elementu [Clear](clear-element-for-namedcaches.md) przed użyciem `add` elementu, aby mieć pewność, że w kolekcji nie ma innych nazwanych pamięci podręcznych. Ten element może być używany w pliku Machine. config i w pliku Web. config.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zdefiniować ustawienia domyślnego `namedCache` wpisu `namedCaches` do kolekcji dla pamięci podręcznej.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<namedCaches >, element (ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
