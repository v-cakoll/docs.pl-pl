---
title: <system.runtime.caching>, element (ustawienia pamięci podręcznej)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153857"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<element> system.runtime.caching (ustawienia pamięci podręcznej)

Zapewnia konfigurację domyślnej <xref:System.Runtime.Caching.ObjectCache> implementacji `memoryCache` w pamięci za pośrednictwem wpisu w pliku konfiguracyjnym.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;**\<>system.runtime.caching**  
  
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
|[\<>memoryCache](memorycache-element-cache-settings.md)|Definiuje element, który jest używany do konfigurowania pamięci <xref:System.Runtime.Caching.MemoryCache> podręcznej, która jest oparta na klasie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracyjne](../configuration-element.md)|Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.|  
  
## <a name="remarks"></a>Uwagi

Klasy w tej przestrzeni nazw umożliwiają korzystanie z urządzeń buforowania, takich jak te w ASP.NET, ale bez zależności od `System.Web` zestawu. Aby uzyskać więcej informacji, zobacz [buforowanie w aplikacjach .NET Framework](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkcje buforowania danych wyjściowych <xref:System.Runtime.Caching> i typy w obszarze nazw są nowe w .NET Framework 4.  
  
## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonfigurować <xref:System.Runtime.Caching.MemoryCache> pamięć podręczną, która jest oparta na klasie. W przykładzie pokazano, jak skonfigurować wystąpienie wpisu `namedCaches` dla pamięci podręcznej. Nazwa pamięci podręcznej jest ustawiona na domyślną `name` nazwę wpisu pamięci podręcznej, ustawiając atrybut na "Domyślny".  
  
Atrybut `cacheMemoryLimitMegabytes` i `physicalMemoryPercentage` atrybut są ustawione na zero. Ustawienie tych atrybutów na <xref:System.Runtime.Caching.MemoryCache> zero oznacza, że heurystyka automatycznego szesnasty są używane domyślnie. Implementacja pamięci podręcznej należy porównać bieżące obciążenie pamięci z bezwzględnych i procentowych limitów pamięci co dwie minuty.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [\<MemoryCache> Element (ustawienia pamięci podręcznej)](memorycache-element-cache-settings.md)
