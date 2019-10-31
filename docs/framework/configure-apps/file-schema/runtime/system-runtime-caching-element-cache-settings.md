---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115508"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<element System. Runtime. cache > (ustawienia pamięci podręcznej)

Zapewnia konfigurację dla domyślnej implementacji <xref:System.Runtime.Caching.ObjectCache> w pamięci za pomocą wpisu `memoryCache` w pliku konfiguracji.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp; **\<system. Runtime. buforowanie >**  
  
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
|[\<elemencie MemoryCache >](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej opartej na klasie <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> konfiguracji \<](../configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi

Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności w zestawie `System.Web`. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkcje i typy wyjściowej pamięci podręcznej w przestrzeni nazw <xref:System.Runtime.Caching> są nowe w .NET Framework 4.  
  
## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na klasie <xref:System.Runtime.Caching.MemoryCache>. W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci. Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej, ustawiając atrybut `name` na "default".  
  
Atrybut `cacheMemoryLimitMegabytes` i atrybut `physicalMemoryPercentage` są ustawione na wartość zero. Ustawienie tych atrybutów na zero oznacza, że domyślnie są używane algorytmy heurystyczne <xref:System.Runtime.Caching.MemoryCache> autodopasowywania. Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.  
  
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

- [\<element > elemencie MemoryCache (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
