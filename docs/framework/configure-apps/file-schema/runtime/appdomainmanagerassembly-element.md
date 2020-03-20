---
title: <appDomainManagerAssembly>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154433"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly> Element
Określa zestaw, który udostępnia menedżera domeny aplikacji dla domyślnej domeny aplikacji w procesie.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
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
|`value`|Atrybut wymagany. Określa wyświetlaną nazwę zestawu, który udostępnia menedżera domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ menedżera domeny aplikacji, należy określić zarówno ten element, jak i [ \<element>appDomainManagerType.](appdomainmanagertype-element.md) Jeśli którykolwiek z tych elementów nie jest określony, drugi jest ignorowany.  
  
 Po załadowaniu domyślnej <xref:System.TypeLoadException> domeny aplikacji jest generowany, jeśli określony zestaw nie istnieje lub jeśli zestaw nie zawiera typu określonego przez [ \<appDomainManagerType>](appdomainmanagertype-element.md) element; i proces nie uruchamia się. Jeśli zestaw zostanie znaleziony, ale informacje o <xref:System.IO.FileLoadException> wersji nie są zgodne, a jest generowany.  
  
 Po określeniu typu menedżera domeny aplikacji dla domyślnej domeny aplikacji inne domeny aplikacji utworzone z domyślnej domeny aplikacji dziedziczą typ menedżera domeny aplikacji. Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> właściwości <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> i, aby określić inny typ menedżera domeny aplikacji dla nowej domeny aplikacji.  
  
 Określenie typu menedżera domeny aplikacji wymaga pełnego zaufania aplikacji. (Na przykład aplikacja uruchomiona na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełnego <xref:System.TypeLoadException> zaufania, a jest generowany.  
  
 Aby uzyskać format nazwy wyświetlanej <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> zestawu, zobacz właściwość.  
  
 Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że menedżer domeny aplikacji `MyMgr` dla domyślnej domeny aplikacji procesu jest typem `AdMgrExample` w zestawie.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<element>> appDomainManagerType](appdomainmanagertype-element.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [SetAppDomainManagerType, metoda](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
