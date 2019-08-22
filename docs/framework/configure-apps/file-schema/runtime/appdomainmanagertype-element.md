---
title: <appDomainManagerType>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663921"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType, element >
Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.  
  
 \<> konfiguracji  
\<runtime>  
\<appDomainManagerType>  
  
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
 Aby określić typ Menedżera domeny aplikacji, należy określić zarówno ten element, jak i [ \<element appDomainManagerAssembly >](appdomainmanagerassembly-element.md) . Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.  
  
 Po załadowaniu domyślnej domeny aplikacji jest zgłaszany, <xref:System.TypeLoadException> Jeśli określony typ nie istnieje w zestawie, który jest określony [ \<przez element appDomainManagerAssembly >](appdomainmanagerassembly-element.md) , a proces nie zostanie uruchomiony.  
  
 W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji. Użyj właściwości <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> i, aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
  
 Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie. (Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, <xref:System.TypeLoadException> jest zgłaszany.  
  
 Format typu i przestrzeni nazw jest tym samym formatem, który jest używany dla <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` typem `AdMgrExample` w zestawie.  
  
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
- [\<appDomainManagerAssembly, element >](appdomainmanagerassembly-element.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [SetAppDomainManagerType, metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
