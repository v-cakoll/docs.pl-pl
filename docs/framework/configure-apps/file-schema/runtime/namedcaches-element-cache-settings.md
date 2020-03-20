---
title: <namedCaches>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153961"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> Element (Ustawienia pamięci podręcznej)
Określa zbiór ustawień konfiguracji dla <xref:System.Runtime.Caching.MemoryCache> nazwanych wystąpień. Właściwość <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> odwołuje się do kolekcji ustawień `namedCaches` konfiguracji z jednego lub więcej elementów pliku konfiguracji.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.runtime.caching**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>memoryCache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nazwaneCaches>**  
  
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
|`cacheMemoryLimitMegabytes`|Wartość całkowita określająca maksymalny dopuszczalny rozmiar w megabajtach, <xref:System.Runtime.Caching.MemoryCache> do której może rosnąć wystąpienie. Wartość domyślna to 0, co oznacza, że heurystyka automatycznego <xref:System.Runtime.Caching.MemoryCache> rozmiaru klasy jest używana domyślnie.|  
|`name`|Nazwa pamięci podręcznej.|  
|`physicalMemoryLimitPercentage`|Wartość całkowita z przedziału od 0 do 100, która określa maksymalny procent fizycznie zainstalowanej pamięci komputera, która może być zużywana przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że heurystyka automatycznego <xref:System.Runtime.Caching.MemoryCache> rozmiaru klasy jest używana domyślnie.|  
|`pollingInterval`|Wartość, która wskazuje przedział czasu, po którym implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci, które są ustawione dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "HH:MM:SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-element-for-namedcaches.md)|Dodaje nazwaną pamięć `namedCaches` podręczną do kolekcji dla pamięci podręcznej.|  
|[\<wyraźne>](clear-element-for-namedcaches.md)|Czyści `namedCaches` kolekcję dla pamięci podręcznej.|  
|[\<usuń>](remove-element-for-namedcaches.md)|Usuwa wpis nazwanej pamięci `namedCaches` podręcznej z kolekcji dla pamięci podręcznej.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracyjne](../configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
|[\<>memoryCache](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie.|  
|[\<>system.runtime.caching](system-runtime-caching-element-cache-settings.md)|Zawiera typy, które umożliwiają implementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w program .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Sekcja konfiguracji pamięci podręcznej pliku Web.config `remove`może `clear` zawierać `add` `namedCaches` i atrybuty kolekcji. Każdy `namedCaches` wpis jest jednoznacznie `name` identyfikowany przez atrybut.  
  
 Można pobrać wystąpienia wpisów pamięci podręcznej, odwołując się do informacji w plikach konfiguracji aplikacji. Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracyjnym. Domyślne wystąpienie pamięci podręcznej jest <xref:System.Runtime.Caching.MemoryCache.Default%2A> wystąpienie, które jest zwracane z właściwości.  
  
 Jeśli ustawisz atrybut name na "default", element używa domyślnego wystąpienia pamięci podręcznej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak ustawić nazwę pamięci podręcznej `name` na domyślną nazwę wpisu pamięci podręcznej, ustawiając atrybut na "domyślny".  
  
 Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryPercentage` atrybut są ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że używane <xref:System.Runtime.Caching.MemoryCache> są heurystyki autosizing klasy. Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci względem bezwzględnych i procentowych limitów pamięci co dwie minuty.  
  
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

- [\<MemoryCache> Element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
