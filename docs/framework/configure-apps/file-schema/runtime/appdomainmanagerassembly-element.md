---
title: <appDomainManagerAssembly> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 7ba52cdf0102af05954509a11fa90e9b8a337876
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118316"
---
# <a name="appdomainmanagerassembly-element"></a>\<element > appDomainManagerAssembly
Określa zestaw, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany. Określa nazwę wyświetlaną zestawu, który udostępnia Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ Menedżera domeny aplikacji, należy określić zarówno element, jak i [\<appDomainManagerType >](appdomainmanagertype-element.md) . Jeśli jeden z tych elementów nie zostanie określony, drugi zostanie zignorowany.  
  
 Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest zgłaszany, jeśli określony zestaw nie istnieje lub jeśli zestaw nie zawiera typu określonego przez [\<appDomainManagerType >](appdomainmanagertype-element.md) elementu; proces kończy się niepowodzeniem i nie można go uruchomić. Jeśli zestaw zostanie znaleziony, ale informacje o wersji nie są zgodne, zostanie zgłoszony <xref:System.IO.FileLoadException>.  
  
 W przypadku określenia typu Menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji. Użyj właściwości <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>, aby określić inny typ Menedżera domeny aplikacji dla nowej domeny aplikacji.  
  
 Określenie typu Menedżera domeny aplikacji wymaga, aby aplikacja miała pełne zaufanie. (Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego zaufania, zostanie zgłoszony <xref:System.TypeLoadException>.  
  
 Aby uzyskać format nazwy wyświetlanej zestawu, zapoznaj się z właściwością <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.  
  
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
- [\<element > appDomainManagerType](appdomainmanagertype-element.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [SetAppDomainManagerType, metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
