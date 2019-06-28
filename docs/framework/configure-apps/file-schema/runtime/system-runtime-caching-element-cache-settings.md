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
ms.openlocfilehash: cbb977e05fa54b726b0cd584d287dc00c8ced995
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423251"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System.Runtime.Caching >, Element (ustawienia pamięci podręcznej)

Udostępnia konfigurację dla domyślnej w pamięci <xref:System.Runtime.Caching.ObjectCache> wdrożenia za pośrednictwem `memoryCache` wpisu w pliku konfiguracji.  
  
 \<Konfiguracja >  
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
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci podręcznej, który jest oparty na <xref:System.Runtime.Caching.MemoryCache> klasy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Konfiguracja >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.|  
  
## <a name="remarks"></a>Uwagi

Klasy w tej przestrzeni nazw zapewniają sposób na korzystanie z pamięci podręcznej urządzenia, podobnie jak w programie ASP.NET, ale bez zależności `System.Web` zestawu. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Zapisywanie funkcji i typów w pamięci podręcznej danych wyjściowych <xref:System.Runtime.Caching> przestrzeni nazw są nowością w programie .NET Framework 4.  
  
## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną, która jest oparta na <xref:System.Runtime.Caching.MemoryCache> klasy. W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpis dla pamięci podręcznej. Nazwę pamięci podręcznej jest ustawiona na domyślną nazwę wpisu pamięci podręcznej, ustawiając `name` atrybutu "Default".  
  
`cacheMemoryLimitMegabytes` Atrybutu i `physicalMemoryPercentage` atrybutu jest równa zero. Ustawienia te atrybuty zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> domyślnie są używane algorytmy heurystyczne automatyczne określanie rozmiaru. Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci względem limity pamięci bezwzględne i opartych na procentach co dwie minuty.  
  
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

- [\<memoryCache >, Element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
