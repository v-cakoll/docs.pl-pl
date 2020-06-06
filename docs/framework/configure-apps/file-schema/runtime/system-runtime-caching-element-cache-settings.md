---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153857"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.caching>, element (ustawienia pamięci podręcznej)

Zapewnia konfigurację dla domyślnej implementacji w pamięci <xref:System.Runtime.Caching.ObjectCache> za pomocą `memoryCache` wpisu w pliku konfiguracji.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
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
|[\<configuration>](../configuration-element.md)|Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi

Klasy w tej przestrzeni nazw zapewniają sposób używania obiektów pamięci podręcznej, takich jak te w ASP.NET, ale bez zależności od `System.Web` zestawu. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkcje i typy wyjściowej pamięci podręcznej w <xref:System.Runtime.Caching> przestrzeni nazw są nowe w .NET Framework 4.  
  
## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować pamięć podręczną opartą na <xref:System.Runtime.Caching.MemoryCache> klasie. W przykładzie pokazano, jak skonfigurować wystąpienie `namedCaches` wpisu dla pamięci podręcznej pamięci. Nazwa pamięci podręcznej jest ustawiana na domyślną nazwę wpisu pamięci podręcznej przez ustawienie `name` atrybutu na wartość "domyślny".  
  
`cacheMemoryLimitMegabytes`Atrybut i `physicalMemoryPercentage` atrybut są ustawione na zero. Ustawienie tych atrybutów na zero oznacza, że <xref:System.Runtime.Caching.MemoryCache> algorytmy autozmiany rozmiarów są używane domyślnie. Implementacja pamięci podręcznej powinna porównać bieżące obciążenie pamięci dla limitów pamięci bezwzględnej i wartości procentowej co dwie minuty.  
  
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

- [\<memoryCache>— Element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
