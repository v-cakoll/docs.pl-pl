---
title: <appDomainManagerType> Element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118244"
---
# <a name="appdomainmanagertype-element"></a>\<element > appDomainManagerType
Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany. Określa nazwę typu, w tym przestrzeń nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ Menedżera domeny aplikacji, należy określić zarówno element, jak i [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) . Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.  
  
 Podczas ładowania domyślnej domeny aplikacji <xref:System.TypeLoadException> jest zgłaszany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu; proces kończy się niepowodzeniem i nie można go uruchomić.  
  
 W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji. Użyj właściwości <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>, aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji.  
  
 Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie. (Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, zostanie zgłoszony <xref:System.TypeLoadException>.  
  
 Format typu i przestrzeni nazw jest tym samym formatem, który jest używany dla właściwości <xref:System.Type.FullName%2A?displayProperty=nameWithType>.  
  
 Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest typem `MyMgr` w zestawie `AdMgrExample`.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<element > appDomainManagerAssembly](appdomainmanagerassembly-element.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [SetAppDomainManagerType, metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
