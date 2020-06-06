---
title: <namedCaches>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153961"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches>, element (ustawienia pamięci podręcznej)
Określa kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Właściwość odwołuje się do kolekcji ustawień konfiguracji z co najmniej jednego `namedCaches` elementu pliku konfiguracji.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
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
|`cacheMemoryLimitMegabytes`|Wartość całkowita, która określa maksymalny dopuszczalny rozmiar (w megabajtach), do którego wystąpienie <xref:System.Runtime.Caching.MemoryCache> może się rozwijać. Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne autozmiany rozmiarów <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.|  
|`name`|Nazwa pamięci podręcznej.|  
|`physicalMemoryLimitPercentage`|Wartość całkowita z zakresu od 0 do 100, która określa maksymalną wartość procentową fizycznie zainstalowanej pamięci komputera, która może być używana przez pamięć podręczną. Wartość domyślna to 0, co oznacza, że algorytmy heurystyczne autozmiany rozmiarów <xref:System.Runtime.Caching.MemoryCache> klasy są używane domyślnie.|  
|`pollingInterval`|Wartość, która wskazuje przedział czasu, po upływie którego implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci z limitami pamięci bezwzględnej i procentową ustawioną dla wystąpienia pamięci podręcznej. Ta wartość jest wprowadzana w formacie "gg: MM: SS".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Dodaje nazwaną pamięć podręczną do `namedCaches` kolekcji dla pamięci podręcznej pamięci.|  
|[\<clear>](clear-element-for-namedcaches.md)|Czyści `namedCaches` kolekcję dla pamięci podręcznej pamięci.|  
|[\<remove>](remove-element-for-namedcaches.md)|Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Zawiera typy, które umożliwiają zaimplementowanie buforowania danych wyjściowych w aplikacjach wbudowanych w .NET Framework.|  
  
## <a name="remarks"></a>Uwagi  
 Sekcja konfiguracja pamięci podręcznej pamięci w pliku Web. config może `add` zawierać `remove` `clear` atrybuty dla kolekcji, i `namedCaches` . Każdy `namedCaches` wpis jest jednoznacznie identyfikowany przez `name` atrybut.  
  
 Wystąpienia wpisów pamięci podręcznej pamięci można pobrać, odwołując się do informacji w plikach konfiguracji aplikacji. Domyślnie tylko domyślne wystąpienie pamięci podręcznej ma wpis w pliku konfiguracji. Domyślne wystąpienie pamięci podręcznej jest wystąpieniem zwracanym z <xref:System.Runtime.Caching.MemoryCache.Default%2A> właściwości.  
  
 Jeśli ustawisz atrybut name na "default", element używa domyślnego wystąpienia pamięci podręcznej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak ustawić nazwę pamięci podręcznej na domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".  
  
 `cacheMemoryLimitMegabytes`Atrybut i `physicalMemoryPercentage` atrybut są ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że używane są heurystyke autowymiarowania <xref:System.Runtime.Caching.MemoryCache> klasy. Implementacja pamięci podręcznej porównuje bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.  
  
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

- [\<memoryCache>— Element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
