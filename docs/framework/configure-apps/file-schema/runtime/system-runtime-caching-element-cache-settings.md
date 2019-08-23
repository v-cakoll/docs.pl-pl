---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ead643afd34b4c3422d85e6f7876879de477ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927242"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System. Runtime. cache >, element (ustawienia pamięci podręcznej)

Zapewnia konfigurację dla domyślnej implementacji w pamięci <xref:System.Runtime.Caching.ObjectCache> `memoryCache` za pomocą wpisu w pliku konfiguracji.  
  
 \<> konfiguracji  
\<system.runtime.caching>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty

`None`  

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na <xref:System.Runtime.Caching.MemoryCache> klasie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> konfiguracji](../configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi

Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności `System.Web` od zestawu. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkcje i typy wyjściowej pamięci podręcznej w <xref:System.Runtime.Caching> przestrzeni nazw są nowe w .NET Framework 4.  
  
## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na <xref:System.Runtime.Caching.MemoryCache> klasie. W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci. Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej `name` przez ustawienie atrybutu na wartość "domyślny".  
  
`cacheMemoryLimitMegabytes` Atrybut`physicalMemoryPercentage` i atrybut są ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie. Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.  
  
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

- [\<Elemencie MemoryCache >, element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
