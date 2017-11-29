---
title: "&lt;namedCaches&gt; elementu (ustawienia pamięci podręcznej)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bdafddcb05dd50f059c9f6804573beec085a4a2a
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; elementu (ustawienia pamięci podręcznej)
Określa kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Właściwość odwołuje się zestaw ustawień konfiguracji z jednego lub kilku `namedCaches` elementów w pliku konfiguracji.  
  
 \<Konfiguracja >  
\<System.Runtime.Caching — >  
\<memoryCache >  
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
|`cacheMemoryLimitMegabytes`|Wartość całkowita określająca maksymalny dozwolony rozmiar w megabajtach, które wystąpienie <xref:System.Runtime.Caching.MemoryCache> odpowiednio do. Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy jest używany domyślnie.|  
|`name`|Nazwa pamięci podręcznej.|  
|`physicalMemoryLimitPercentage`|Wartość całkowitą pomiędzy 0 a 100 określająca maksymalny procent pamięci fizycznie zainstalowanym komputerze, który może być zużyte przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy jest używany domyślnie.|  
|`pollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementację buforu porównuje bieżącego obciążenia pamięci limitów bezwzględne lub wartości procentowej pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "Gg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Dodaje nazwany pamięci podręcznej, aby `namedCaches` kolekcji dla pamięci podręcznej.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Czyści `namedCaches` kolekcji dla pamięci podręcznej.|  
|[\<Usuń >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Usuwa wpis w pamięci podręcznej o nazwie z `namedCaches` kolekcji dla pamięci podręcznej.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<memoryCache >](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Sekcja konfiguracji pamięci podręcznej pamięci w pliku Web.config może zawierać `add`, `remove`, i `clear` atrybutów `namedCaches` kolekcji. Każdy `namedCaches` wpis jest unikatowo identyfikowana przez `name` atrybutu.  
  
 Za pomocą odwołań do informacji w plikach konfiguracji aplikacji można pobrać wystąpień wpisy w pamięci podręcznej pamięci. Domyślnie tylko domyślnego wystąpienia pamięci podręcznej ma wpis w pliku konfiguracji. Domyślne wystąpienie pamięci podręcznej jest wystąpienia, która jest zwracana z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.  
  
 Jeśli zostanie ustawiony atrybut name "default", element używa domyślnego wystąpienia pamięci podręcznej pamięci.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób ustawioną domyślną nazwę wpisu pamięci podręcznej nazwę pamięci podręcznej przez ustawienie `name` atrybutu "default".  
  
 `cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu zostaną ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że Algorytm heurystyczny automatyczna zmiana rozmiaru z <xref:System.Runtime.Caching.MemoryCache> klasy są używane. Implementacja pamięci podręcznej porównuje bieżącego obciążenia pamięci na wartości bezwzględne lub wartości procentowej pamięci co dwie minuty.  
  
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
