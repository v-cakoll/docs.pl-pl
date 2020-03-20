---
title: <add>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154508"
---
# <a name="add-element-for-namedcaches"></a>\<dodaj element> dla \<nazwanychcach>
Dodaje `namedCache` wpis do `namedCaches` kolekcji dla pamięci podręcznej.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>memoryCache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nazwaneCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**  
  
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
|`CacheMemoryLimitMegabytes`|Wartość całkowita określająca maksymalny dozwolony rozmiar (w megabajtach), <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie. Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że klasy autosizing heurystyki są używane domyślnie.|  
|`Name`|Nazwa pamięci podręcznej.|  
|`PhysicalMemoryLimitPercentage`|Wartość całkowita z przedziału od 0 do 100, która określa maksymalny procent fizycznie zainstalowanej pamięci komputera, która może być zużywana przez pamięć podręczną. Wartość domyślna to 0, <xref:System.Runtime.Caching.MemoryCache> co oznacza, że klasy autosizing heurystyki są używane domyślnie.|  
|`PollingInterval`|Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 `None`  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<nazwaneCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji <xref:System.Runtime.Caching.MemoryCache> dla nazwanych wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 Element `add` dodaje wpis do `namedCaches` kolekcji dla pamięci podręcznej. Można użyć [clear](clear-element-for-namedcaches.md) element przed `add` użyciem elementu, aby mieć pewność, że nie ma żadnych innych nazwanych pamięci podręcznych w kolekcji. Ten element może być używany w pliku machine.config i w pliku Web.config.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, `namedCache` jak zdefiniować ustawienia domyślnego wpisu `namedCaches` do kolekcji dla pamięci podręcznej.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [\<namedCaches> Element (Ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
