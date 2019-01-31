---
title: <appDomainManagerType>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a3bf60986b571b473561d4258a76624bbfc982
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262481"
---
# <a name="appdomainmanagertype-element"></a>\<appdomainmanagertype — > Element
Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.  
  
 \<Konfiguracja >  
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
|`value`|Atrybut wymagany. Określa nazwę typu, włącznie z przestrzenią nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ Menedżer domeny aplikacji, należy określić zarówno ten element i [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu. Jedną z tych elementów nie zostanie określony, druga jest ignorowana.  
  
 Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest generowany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu; a proces zakończy się niepowodzeniem do początek.  
  
 Kiedy określasz typ Menedżera domeny aplikacji dla domyślnej domeny aplikacji, innych domenach aplikacji, utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji. Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> właściwości, aby określić typ Menedżera domeny w innej aplikacji dla nowej domeny aplikacji.  
  
 Określanie typu Menedżer domeny aplikacji wymaga aplikacja miała pełne zaufanie. (Na przykład aplikację działającą na pulpicie ma pełne zaufanie). Jeśli aplikacja nie ma pełne zaufanie <xref:System.TypeLoadException> zgłaszany.  
  
 Format typu i przestrzeni nazw jest tym samym formacie, który służy do <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` wpisać `AdMgrExample` zestawu.  
  
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
- [\<appdomainmanagerassembly — > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [SetAppDomainManagerType, metoda](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
